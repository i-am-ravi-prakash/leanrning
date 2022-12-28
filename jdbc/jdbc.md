### JDBC stands for Java Database Connectivity. It's an API provided by Oracle for Java applications to connect with different sets of databases.

To connect any Java application with database, we need to follow the below steps:

1. **Driver class**: The driver class for the database. For MySQL database, the driver class will be **com.mysql.jdbc.Driver**.
2. **Connection URL**: The connection URL for the mysql database is **jdbc:mysql://localhost:3306/sonoo** where jdbc is the API, mysql is the database, localhost is the server name on which mysql is running, we may also use IP address, 3306 is the port number and sonoo is the database name. We may use any database, in such case, we need to replace the sonoo with our database name.
3. **Username**: The default username for the mysql database is root.
4. **Password**: It is the password which is used to connect to the database.

Below is a sample code to demonstrate how jdbc works:

```
import java.sql.*;

public class JDBCExample {
   static final String DB_URL = "jdbc:mysql://localhost/TUTORIALSPOINT";
   static final String DB_USERNAME = "guest";
   static final String DB_PASSWORD = "guest123";
   static final String QUERY = "SELECT id, first, last, age FROM Employees";

   public static void main(String[] args) {
      // Open a connection
      try(Connection conn = DriverManager.getConnection(DB_URL, USER, PASS);
         Statement stmt = conn.createStatement();
         ResultSet rs = stmt.executeQuery(QUERY);) {
         // Extract data from result set
         while (rs.next()) {
            // Retrieve by column name
            System.out.print("ID: " + rs.getInt("id"));
            System.out.print(", Age: " + rs.getInt("age"));
            System.out.print(", First: " + rs.getString("first"));
            System.out.println(", Last: " + rs.getString("last"));
         }
      } catch (SQLException e) {
         e.printStackTrace();
      } 
   }
}
```
