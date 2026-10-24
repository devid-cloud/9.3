# 9.3
9.3
import java.sql.*;

class JDBCDelete {
    public static void main(String args[]) {
        try {
            // Load JDBC Driver
            Class.forName("com.mysql.cj.jdbc.Driver");

            // Connect to database
            Connection con = DriverManager.getConnection(
                "jdbc:mysql://localhost:3306/studentdb",
                "root",
                "password"
            );

            // Delete query
            String sql = "DELETE FROM student WHERE id = ?";

            PreparedStatement ps = con.prepareStatement(sql);

            // ID of the record to delete
            ps.setInt(1, 101);

            // Execute delete query
            int n = ps.executeUpdate();

            if (n > 0)
                System.out.println("Record deleted successfully!");
            else
                System.out.println("Record not found!");

            // Close connection
            ps.close();
            con.close();
        }
        catch(Exception e) {
            System.out.println(e);
        }
    }
}
