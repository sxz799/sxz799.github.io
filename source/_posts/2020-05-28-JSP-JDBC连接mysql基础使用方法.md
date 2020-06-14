---
title: JSP-JDBC连接mysql基础使用方法
copyright: true
date: 2020-05-28 15:22:37
tags:
- JDBC 数据库
categories:
- JAVA
comments:
password:
---

## 一、下载必备jar包
下载 mysql-connector-java-5.1.48-bin.jar
## 二、编写JDBC工具类
代码如下
```
/**
 * 导入包
 */
import java.sql.Connection;
import java.sql.DriverManager;

public class DBHelper 
{
	//配置静态变量 分别是驱动名称，url 用户名 密码，初始化Connection连接对象
	private static final String driver = "com.mysql.jdbc.Driver";
	private static final String url = "jdbc:mysql://localhost:3306/ccls?useSSL=false";
	private static final String username = "root";
	private static final String password = "123456";
	private static Connection conn=null; 
		
	//静态代码块，负责加载驱动
	static {
		try {
			Class.forName(driver);
		}
		catch (Exception ex) {
			
			ex.printStackTrace();
		}
	}
	//创建获取连接方法getConnection()，返回数据库链接对象
	public static Connection getConnection() throws Exception {
		if(conn==null)
		{
			conn = DriverManager.getConnection(url,username,password);
			return conn;
		}
		return conn;
	
	}
	/**
	 * 测试数据库连接
	 */
	public static void main(String[] args) {
		try {
			Connection conn = DBHelper.getConnection();
			if(conn!=null)
				System.out.println("数据库链接正常");
			else {
				System.out.println("数据库链接异常");
			}
		}
		catch (Exception ex) {
			ex.printStackTrace();
		}
	}
	//资源释放方法
	public static void DBClose(ResultSet rs ,PreparedStatement ps,Connection conn) {
        if (rs != null) {
            try {
                rs.close();
                rs = null;
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
        if (ps != null) {
            try {
                ps.close();
                ps = null;
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
        if (conn != null) {
            try {
                conn.close();
                conn = null;
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
    }
}
```
## 三、使用工具类实例
```
/**
 * 判断用户登录函数
 */
	public boolean checkUser(String name, String pwd) { 
		Connection conn = null;
		PreparedStatement ps = null;
		ResultSet rs = null;
		try {
			conn = DBHelper.getConnection();
			String sql = "SELECT * FROM user WHERE name =? AND pwd = ?";
			ps = conn.prepareStatement(sql);
			ps.setString(1, name);
			ps.setString(2, pwd);
			rs = ps.executeQuery();
			if (rs.next()) {
				return true;
			} else {
				return false;
			}
		} catch (Exception e) {
			e.printStackTrace();
			return false;
		} finally {
			DBHelper.DBClose(rs,ps,conn);
		}
	}

```
