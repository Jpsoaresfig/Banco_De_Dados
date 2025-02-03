package application;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.text.ParseException;
import java.text.SimpleDateFormat;

import db.DB;

public class program {

	public static void main(String[] args) {
	//inserir dados.
		SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy"); 
		Connection conn = null;
		PreparedStatement st = null;
		try {
			conn = DB.getConnection();//conecotu com banco 
			
			st = conn.prepareStatement(
					"INSERT INTO seller"
					+"(Name, Email, BirthDate, BaseSalary, DepartmentId)"
					+ "VALUES"
					+ "(?,?,?,?,?)",Statement.RETURN_GENERATED_KEYS);
			st.setString(1, "Carl Purple");
			st.setString(2, "Carl@gmail.com");
			st.setDate(3, new java.sql.Date(sdf.parse("22/04/1985").getTime()));//atribuindo valores a data
			st.setDouble(4, 3000.0);
			st.setInt(5, 4);
			
		int rowAffected =st.executeUpdate();
		
		if(rowAffected>0) {
		ResultSet rs =	st.getGeneratedKeys();//retorna o objeto do tipo resultset
		while(rs.next()) {
			int id = rs.getInt(1);
			System.out.println("Done! ID = " + id);
		}
		}else {
			System.out.println("No rown affected!");
		}
		}catch(SQLException e) {
			e.printStackTrace();
		}catch(ParseException e) {
			e.printStackTrace();
		}finally {
			DB.closeStatement(st);
			DB.closeConnection();
		}

}}
