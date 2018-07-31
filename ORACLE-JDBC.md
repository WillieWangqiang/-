# ORACLE JDBC
package com.application.jdbc.applicationjdbc;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

//JDBC连接数据库，并作简单查询测试
public class ApplicationJdbc {
	public static void main(String[] args) throws ClassNotFoundException, SQLException {
		Class.forName("oracle.jdbc.OracleDriver");//加载Oracle驱动类
		String url = "jdbc:oracle:thin:localhost:1521:orcl";	//数据库连接地址
		String user = "DATA";	//数据库用户名
		String pwd = "DATA";	//数据库密码
		Connection con = DriverManager.getConnection(url,user,pwd);	//获取连接
		System.out.println("连接获取成功...");
		Statement st = con.createStatement();		//从连接中生成Statement实例
		ResultSet rs = st.executeQuery("select BASE_ID,NAME from BA_BASE");	//执行SQL语句查询
		while(rs.next()) {	//展示查询的结果集
			System.out.println(rs.getString("BASE_ID")+","+rs.getString("NAME"));
		}
	}
}
