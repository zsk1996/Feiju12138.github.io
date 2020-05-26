---
title: 【代码】JDBC实现增删改查
categories:
  - Java
date: 2020-05-20 08:20:35
---

## 前言

用JDBC实现增删改查操作

<!-- more -->

## 工具类

``` java
package com.tedu.test;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

public class DBUtil {
   
    static {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
        } catch (ClassNotFoundException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
    }
    
    public static Connection getConnection() {
        String url = "jdbc:mysql://localhost:3306/jdbc?serverTimezone=UTC";
        String username = "root";
        String password = "123456";
        Connection connection = null;
        try {
            connection = DriverManager.getConnection(url, username, password);
        } catch (SQLException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
        return connection;
    }
    
    public static void close(Connection connection, PreparedStatement prepareStatement, ResultSet resultSet) {
        
        if(resultSet != null) {
            try {
                resultSet.close();
            } catch (SQLException e) {
                // TODO Auto-generated catch block
                e.printStackTrace();
            }
        }
        if(prepareStatement != null) {
            try {
                prepareStatement.close();
            } catch (SQLException e) {
                // TODO Auto-generated catch block
                e.printStackTrace();
            }
        }
        if(connection != null) {
            try {
                connection.close();
            } catch (SQLException e) {
                // TODO Auto-generated catch block
                e.printStackTrace();
            }
        }
        
    }
    
}
```

## 模型类

``` java
package com.tedu.test;

public class User {
    
    private int id;
    private String username;
    private String password;
    private String nickname;
    
    public User() {
        
    }

    public User(String username, String password, String nickname) {
        this.username = username;
        this.password = password;
        this.nickname = nickname;
    }

    public User(int id, String username, String password, String nickname) {
        super();
        this.id = id;
        this.username = username;
        this.password = password;
        this.nickname = nickname;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getUsername() {
        return username;
    }

    public void setUsername(String username) {
        this.username = username;
    }

    public String getPassword() {
        return password;
    }

    public void setPassword(String password) {
        this.password = password;
    }

    public String getNickname() {
        return nickname;
    }

    public void setNickname(String nickname) {
        this.nickname = nickname;
    }

    @Override
    public String toString() {
        return "User [id=" + id + ", username=" + username + ", password=" + password + ", nickname=" + nickname + "]";
    }
    
    
}
```

## 主类

``` java
package com.tedu.test;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class TestJdbc {
    
    public static void main(String[] args) {
        
    }
    
    // 添加数据
    public static void add(User user) {
        Connection connection = null;
        PreparedStatement prepareStatement = null;
        String sql = "INSERT INTO NewTable (username, password, nickname) values(?, ?, ?)";
        try {
            connection = DBUtil.getConnection();
            prepareStatement = connection.prepareStatement(sql);
            prepareStatement.setString(1, user.getUsername());
            prepareStatement.setString(2, user.getPassword());
            prepareStatement.setString(3, user.getNickname());
            prepareStatement.executeUpdate();            
        } catch (SQLException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        } finally {
            DBUtil.close(connection, prepareStatement, null);
        }
        
    }
    
    // 删除数据
    public static void delete(int id) {
        Connection connection = null;
        PreparedStatement prepareStatement = null;
        String sql = "DELETE FROM NewTable WHERE id=?";
        try {
            connection = DBUtil.getConnection();
            prepareStatement = connection.prepareStatement(sql);
            prepareStatement.setInt(1, id);
            prepareStatement.executeUpdate();            
        } catch (SQLException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        } finally {
            DBUtil.close(connection, prepareStatement, null);
        }
        
    }
    
    // 修改数据
    public static void update(User user) {
        Connection connection = null;
        PreparedStatement prepareStatement = null;
        String sql = "UPDATE NewTable SET username=?, password=?, nickname=? WHERE id=?";
        try {
            connection = DBUtil.getConnection();
            prepareStatement = connection.prepareStatement(sql);
            prepareStatement.setString(1, user.getUsername());
            prepareStatement.setString(2, user.getPassword());
            prepareStatement.setString(3, user.getNickname());
            prepareStatement.setInt(4, user.getId());
            prepareStatement.executeUpdate();            
        } catch (SQLException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        } finally {
            DBUtil.close(connection, prepareStatement, null);
        }
        
    }
    
    // 查询数据
    public static User load(int id) {
        Connection connection = null;
        PreparedStatement prepareStatement = null;
        String sql = "SELECT * FROM NewTable WHERE id=?";
        ResultSet resultSet = null;
        User user = null;
        try {
            connection = DBUtil.getConnection();
            prepareStatement = connection.prepareStatement(sql);
            prepareStatement.setInt(1, id);
            resultSet = prepareStatement.executeQuery();
            while(resultSet.next()) {
                user = new User();
                user.setId(resultSet.getInt("id"));
                user.setUsername(resultSet.getString("username"));
                user.setPassword(resultSet.getString("password"));
                user.setNickname(resultSet.getString("nickname"));
            }
        } catch (SQLException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        } finally {
            DBUtil.close(connection, prepareStatement, resultSet);
        }
        return user;
    }
    
}
```

## 完成

