---
title: 【代码】SpringBoot项目使用Hikari连接池
categories:
  - Java
date: 2020-09-28 19:31:04
---

## 前言

SpringBoot项目整合数据库连接池后，默认使用Hikari连接池

<!-- more -->

## 配置

- [传送门](/2020/08/28/SpringBoot整合数据库连接池/)

## 使用连接池实现查询

``` java
@Repository// 描述数据层实现类对象
public class DefaultGoodsDao implements GoodsDao {

    @Autowired
    DataSource dataSource;

    /**
     * 查询商品信息，一行记录映射为内存中的一个map对象
     * @return
     */
    @Override
    public List<Map<String, Object>> findGoods() {
        List<Map<String, Object>> list = new ArrayList<>();
        try {
            //1. 获取连接
            Connection connection = dataSource.getConnection();
            //2. 创建statement对象
            Statement statement = connection.createStatement();
            //3. 发送sql
            ResultSet resultSet = statement.executeQuery("SELECT * FROM tb_goods");
            //4. 处理结果
            while(resultSet.next()) {
                int id = resultSet.getInt("id");
                String name = resultSet.getString("name");
                String remark = resultSet.getString("remark");
                Time createdTime = resultSet.getTime("createdTime");
                //System.out.println("id:"+id+" name:"+name+" remark:"+remark+" createdTime"+createdTime);
                Map<String, Object> map = new HashMap<>();
                map.put("id", id);
                map.put("name", name);
                map.put("remark", remark);
                map.put("createdTime", createdTime);
                list.add(map);
            }
            //5. 释放资源
            resultSet.close();
            statement.close();
            connection.close();
        } catch (SQLException e) {
            e.printStackTrace();
            throw new RuntimeException(e);
        }
        return list;
    }

}
```

### 进行简单的封装

``` java
@Repository
public class DefaultGoodsDao implements  GoodsDao{
    @Autowired
    private DataSource dataSource;//hikariCP
    /**查询商品信息,一行记录映射为内存中的一个map对象*/
    public List<Map<String,Object>> findGoods(){
        Connection conn=null;//java.sql.*
        Statement stmt=null;
        ResultSet rs=null;
        String sql="select id,name,remark note,createdTime from tb_goods";
        //1.获取连接(从连接池获取)
        try {
            conn=dataSource.getConnection();
            //2.创建statement对象
            stmt=conn.createStatement();
            //3.发送sql
            rs=stmt.executeQuery(sql);
            //4.处理结果
            List<Map<String,Object>> list=new ArrayList<>();
            while(rs.next()){//循环一次取一行,一行记录映射为一个map对象
                list.add( rowMap(rs));//将存储了一行记录的map对象再存储到list集合
            }
            return list;
        }catch (SQLException e){
            e.printStackTrace();
            throw new RuntimeException(e);//转换为非检查异常(编译时不检测的异常)
        }finally{
            //5. 释放资源
            close(rs,stmt,conn);
        }
    }
    private Map<String,Object> rowMap(ResultSet rs)throws SQLException{
        Map<String,Object> rowMap=new HashMap<>();
        //方法1映射
        //rowMap.put("id",rs.getInt("id"));
        //rowMap.put("name",rs.getString("name"));
        //rowMap.put("remark",rs.getString("remark"));
        //rowMap.put("createdTime",rs.getTimestamp("createdTime"));
        //方法2映射
        ResultSetMetaData rsmd=rs.getMetaData();//获取元数据(包括表中的字段名)
        int columnCount=rsmd.getColumnCount();//获取列的数量
        for(int i=0;i<columnCount;i++){
            rowMap.put(rsmd.getColumnLabel(i+1),rs.getObject(rsmd.getColumnLabel(i+1)));
            //getColumnLabel(i+1);获取表中字段名或字段名对应的别名
        }
        return rowMap;
    }
    private void close(ResultSet rs,Statement stmt,Connection conn){
        if(rs!=null)try{rs.close();}catch(Exception e){e.printStackTrace();}
        if(stmt!=null)try{stmt.close();}catch(Exception e){e.printStackTrace();}
        //这里的连接是返回到了池中
        if(conn!=null)try{conn.close();}catch(Exception e){e.printStackTrace();}
    }
}
```

## 完成

