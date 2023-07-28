import javax.servlet.http.*;
import javax.servlet.*;
import java.io.*;
import java.sql.*;

public class InsertServlet extends HttpServlet{
	public void service(ServletRequest request,ServletResponse response) throws ServletException,IOException {

		PrintWriter out=response.getWriter();
		response.setContentType("text/html");

       //Req.g.p.logic
		int dno=
			Integer.parseInt( request.getParameter("DNO"));
		String dname=request.getParameter("DNAME");
		String dloc=request.getParameter("DLOC");

       //DBLogic For Inserting Rec into dept
	   Connection con=null;
	   PreparedStatement pst=null;

	   try{
	     Class.forName("oracle.jdbc.driver.OracleDriver");
		  
		  con=DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:orcl","scott","Tiger9");

		String query="INSERT INTO DEPT VALUES(?,?,?)";	
  	    pst=con.prepareStatement(query);

		pst.setInt(1,dno);
		pst.setString(2,dname);
		pst.setString(3,dloc);

		pst.executeUpdate();
		out.print("<h1 align=center>"+dname+" Rec is inserted... </h1>");

	   }
	   catch(ClassNotFoundException cnfe)
		{ out.print("<h2 align=center>"+cnfe+"</h2>");}

	   catch(SQLException se)
		{ out.print("<h2 align=center>"+se+"</h2>");}

	   finally{
         try{
		   if (pst!=null)
		        {	pst.close();   }
		   if(con!=null)
		       {con.close(); }
		   }
		 catch(Exception e)
		    {}
	   }

		out.close();
	}
}