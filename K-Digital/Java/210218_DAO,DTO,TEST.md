#DAO / DTO / TEST

```java
import dao.TMemberDAO;
import dto.TMemberDTO;

public class TMemberTest {

	public static void main(String[] args) {
//		//전체조회
//		TMemberDAO dao = new TMemberDAO();
//		ArrayList<TMemberDTO> mlist = dao.queryTMembers();
//		for (TMemberDTO m : mlist) {
//			System.out.println(m);
//		}

		// 삽입
//		TMemberDAO dao = new TMemberDAO();
//		int rcnt = dao.insertTMember(new TMemberDTO("yoo","1212","유재석","yoo@naver.com","21/02/18"));
//		if(rcnt>0) {
//			System.out.println("삽입 성공");
//		} else {
//			System.out.println("삽입 실패");
//		}

		// 갱신
//		TMemberDAO dao = new TMemberDAO();
//		int rcnt = dao.updateTMemberPwd("yoo","9999");
//		if(rcnt>0) {
//			System.out.println("갱신 성공");
//		} else {
//			System.out.println("갱신 실패");
//		}

		// 삭제
//		TMemberDAO dao = new TMemberDAO();
//		int rcnt = dao.deleteTMember("yoo");
//		if (rcnt > 0) {
//			System.out.println("삭제 성공");
//		} else {
//			System.out.println("삭제 실패");
//		}
		
		//검색
		TMemberDAO dao = new TMemberDAO();
		TMemberDTO member = dao.queryTMember("song");
		if (member!=null) {
			System.out.println(member);
		} else {
			System.out.println("조회 실패");
		}

	}
}
```

```java
package dao;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.ArrayList;

import dto.TMemberDTO;

public class TMemberDAO {
	Connection conn;

	public TMemberDAO() {
		try {
			Class.forName("oracle.jdbc.OracleDriver");
			conn = DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:xe", "hr", "hr");
		} catch (ClassNotFoundException e) {
			e.printStackTrace();
		} catch (SQLException e) {
			e.printStackTrace();
		}

	}

	public TMemberDTO queryTMember(String id) {
		PreparedStatement pstmt = null;
		ResultSet rset = null;
		TMemberDTO member = null;
		String sql = "select * from t_member where id=?";
		try {
			pstmt = conn.prepareStatement(sql);
			pstmt.setString(1, id);
			rset = pstmt.executeQuery();
			if (rset.next()) {
				member = new TMemberDTO();
				member.setId(rset.getString(1));
				member.setPwd(rset.getString("pwd"));
				member.setName(rset.getString("name"));
				member.setEmail(rset.getString("email"));
				member.setJoindate(rset.getString("joindate"));
			}

		} catch (SQLException e) {
			e.printStackTrace();
		} finally {
			try {
				if (rset != null)
					rset.close();
				if (pstmt != null)
					pstmt.close();
				if (conn != null)
					conn.close();
			} catch (SQLException e) {
				e.printStackTrace();
			}
		}
		return member;
	}

	public ArrayList<TMemberDTO> queryTMembers() {
		Statement stmt = null;
		ResultSet rset = null;
		String sql = "select * from t_member";
		ArrayList<TMemberDTO> list = new ArrayList<>();
		try {
			stmt = conn.createStatement();
			rset = stmt.executeQuery(sql);
			while (rset.next()) {
				TMemberDTO mem = new TMemberDTO();
				mem.setId(rset.getString("id"));
				mem.setEmail(rset.getString("email"));
				mem.setPwd(rset.getString("pwd"));
				mem.setName(rset.getString("name"));
				mem.setJoindate(rset.getString("joindate"));
				list.add(mem);
			}
		} catch (SQLException e) {
			e.printStackTrace();
		} finally {
			try {
				if (rset != null)
					rset.close();
				if (stmt != null)
					stmt.close();
				if (conn != null)
					conn.close();
			} catch (SQLException e) {
				e.printStackTrace();
			}
		}
		return list;
	}

	public int insertTMember(TMemberDTO member) {
		String sql = "insert into t_member values(?,?,?,?,?)";
		PreparedStatement pstmt = null;
		int rcnt = 0;
		try {
			pstmt = conn.prepareStatement(sql);
			pstmt.setString(1, member.getId());
			pstmt.setString(2, member.getPwd());
			pstmt.setString(3, member.getName());
			pstmt.setString(4, member.getEmail());
			pstmt.setString(5, member.getJoindate());
			rcnt = pstmt.executeUpdate();
		} catch (SQLException e) {
			e.printStackTrace();
		} finally {
			try {
				if (pstmt != null)
					pstmt.close();
				if (conn != null)
					conn.close();
			} catch (SQLException e) {
				e.printStackTrace();
			}
		}
		return rcnt;
	}

	public int updateTMemberPwd(String id, String pwd) {
		String sql = "update t_member set pwd=? where id=?";
		PreparedStatement pstmt = null;
		int rcnt = 0;
		try {
			pstmt = conn.prepareStatement(sql);
			pstmt.setString(1, pwd);
			pstmt.setString(2, id);
			rcnt = pstmt.executeUpdate();
		} catch (SQLException e) {
			e.printStackTrace();
		} finally {
			try {
				if (pstmt != null)
					pstmt.close();
				if (conn != null)
					conn.close();
			} catch (SQLException e) {
				e.printStackTrace();
			}
		}
		return rcnt;
	}

	public int deleteTMember(String id) {
		String sql = "delete from t_member where id=?";
		PreparedStatement pstmt = null;
		int rcnt = 0;
		try {
			pstmt = conn.prepareStatement(sql);
			pstmt.setString(1, id);
			rcnt = pstmt.executeUpdate();
		} catch (SQLException e) {
			e.printStackTrace();
		} finally {
			try {
				if (pstmt != null)
					pstmt.close();
				if (conn != null)
					conn.close();
			} catch (SQLException e) {
				e.printStackTrace();
			}
		}
		return rcnt;
	}

}
```

```java
package dto;

public class TMemberDTO {
	String id;
	String pwd;
	String name;
	String email;
	String joindate;

	public TMemberDTO() {
	}

	public TMemberDTO(String id, String pwd, String name, String email, String joindate) {
		this.id = id;
		this.pwd = pwd;
		this.name = name;
		this.email = email;
		this.joindate = joindate;
	}

	public String getId() {
		return id;
	}

	public void setId(String id) {
		this.id = id;
	}

	public String getPwd() {
		return pwd;
	}

	public void setPwd(String pwd) {
		this.pwd = pwd;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public String getEmail() {
		return email;
	}

	public void setEmail(String email) {
		this.email = email;
	}

	public String getJoindate() {
		return joindate;
	}

	public void setJoindate(String joindate) {
		this.joindate = joindate;
	}

	@Override
	public String toString() {
		return "ID: " + id + ", PWD:" + pwd + ", NAME:" + name + ", EMAIL:" + email + ", JOINDATE:" + joindate;
	}

}

```



