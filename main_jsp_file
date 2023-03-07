package JAVAFD.oldjvfd;

import java.sql.*; //sql 라이브러리 import시키는거
import jakarta.servlet.ServletException; //webservlet 라이브러리 import 시키는거
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import java.io.IOException; // try - catch 형식으로 구문을 던지고 에러가 발생햇을때 받는 형식을 import 한거.
import java.io.PrintWriter; //소켓핸들링으로 소켓에 적는거

@WebServlet(“/WEBlogin”) //웹서블릿을 이름 ‘weblogin’으로 설정
public class WEBlogin extends HttpServlet {
	private static final long serialVersionUID = 1L;
	public WEBlogin() {
		super();
	}

protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException { //GET방식으로 패킷을 받앗을 경우 실행하는 코드
		request.setCharacterEncoding(“UTF-8”); //인코딩을 UTF8로 설정
		response.setCharacterEncoding(“UTF-8”);
		response.setContentType(“text/html; charset=UTF-8”);
		String userid = request.getParameter(“userid”); //request 파라미터 userid 세팅
		String userpw = request.getParameter(“userpw”);//request 파라미터 userpw 세팅
		String id = “”;
		String pw = “”;
	    String group = “”;
	    String name = “”;
		try{
			Connection conn = null;
			try{
				Class.forName(“com.mysql.jc.jdbc.Driver”); /*mysql버전이 8버전이상일 경우 ‘com.mysql.cj.jdbc.Driver’을 입력하고, mysql버전이 7버전이하일 경우 ‘com.mysql.jdbc.Driver’을 입력한다. */
				String dburl = “jdbc:mysql://localhost:3306/데이터베이스이름;
				String dbid = “접속자ID”;
				String dbpw = “접속자PW”;
				conn = DriverManager.getConnection(dburl, dbid, dbpw); //DB접속문
			}catch(Exception e){
				e.printStackTrace();
			}
			PreparedStatement pstmt = null;
			ResultSet rs = null;
			String sql = “SELECT * FROM webtable WHERE user_id=? AND user_pw=?”;
			pstmt = conn.prepareStatement(sql);
			pstmt.setString(1, userid);
			pstmt.setString(2, userpw);
			rs = pstmt.executeQuery();
			while(rs.next()) {
				id += rs.getString(“user_id”);
				pw += rs.getString(“user_pw”);
				group += rs.getString(“user_group”);
				name += rs.getString(“user_name”);
			}
	}catch(Exception e){
			e.printStackTrace();
		}
//결과값 전달(#중요사항 참조)
		if(id.equals(userid) && pw.equals(userpw)){
			PrintWriter pwt = response.getWriter(); //소켓에 패킷내용을 적겟다를 선언
			pwt.write(“text/html”); //전달할 내용 들
			pwt.write(“<html><head>”);
			pwt.write(“<body>”);
			pwt.write(“OKAY”);
			pwt.write(“%vltrue,”+group+”,,”+name+”,,,,,^^^”);
			pwt.write(“</body>”);
			pwt.write(“</head></html>”);
			pwt.close();
		}else{
			PrintWriter pwt = response.getWriter(); 
			pwt.write(“FAIL”);
			pwt.close();
		}
}

protected void doPost(HttpServletRequest request, Http ServletResponse response) throws ServletException, IOException { //POST방식으로 패킷을 전달받았을때 실행하는 코드로 GET과 동일하게 설정해줌
		doGet(request, response);
	}
}
