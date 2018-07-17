# -
package com.application.jdbc.applicationjdbc;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

//JDBC连接数据库，并作简单查询测试
public class ApplicationJdbc {
	public static void main(String[] args) throws ClassNotFoundException, SQLException {
		Class.forName("oracle.jdbc.OracleDriver");
		String url = "jdbc:oracle:thin:@192.168.2.6:1521:orcl";
		String user = "JPERPDATA";
		String pwd = "JPERPDATA";
		Connection con = DriverManager.getConnection(url,user,pwd);
		System.out.println("连接获取成功...");
		Statement st = con.createStatement();
		ResultSet rs = st.executeQuery("select BASE_ID,NAME from BA_BASE");
		while(rs.next()) {
			System.out.println(rs.getString("BASE_ID")+","+rs.getString("NAME"));
		}
	}
}
