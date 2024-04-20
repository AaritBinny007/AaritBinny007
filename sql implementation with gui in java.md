import java.sql.*;
import java.util.*;
import javax.swing.*;
import java.awt.event.*;

class EmployeeGUI extends JFrame
{
JLabel empid, name, des, nat, year, sal;
JTextField id, nm, ds, nt, yr, sl;

EmployeeGUI(int eid) throws ClassNotFoundException, SQLException
{
super("Employee Details");
empid = new JLabel("ID:");
name = new JLabel("Name:");
des = new JLabel("Designation:");
nat = new JLabel("Nationality:");
year = new JLabel("Year of joining:");
sal = new JLabel("Salary:");
id = new JTextField(50);
id.setEnabled(false);
nm = new JTextField(50);
nm.setEnabled(false);
ds = new JTextField(50);
ds.setEnabled(false);
nt = new JTextField(50);
nt.setEnabled(false);
yr = new JTextField(50);
yr.setEnabled(false);
sl = new JTextField(50);
sl.setEnabled(false);
add(empid);
add(name);
add(des);
add(nat);
add(year);
add(sal);
add(id);
add(nm);
add(ds);
add(nt);
add(yr);
add(sl);
setLayout(null);
empid.setBounds(10, 10, 200, 20);
id.setBounds(10, 40, 200, 20);
name.setBounds(10, 70, 200, 20);
nm.setBounds(10, 100, 200, 20);
des.setBounds(10, 130, 200, 20);
ds.setBounds(10, 160, 200, 20);
nat.setBounds(10, 190, 200, 20);
nt.setBounds(10, 220, 200, 20);
year.setBounds(10, 250, 200, 20);
yr.setBounds(10, 280, 200, 20);
sal.setBounds(10, 310, 200, 20);
sl.setBounds(10, 340, 200, 20);
setSize(220, 400);
setVisible(true);
setDefaultCloseOperation(EXIT_ON_CLOSE);

Class.forName("com.mysql.cj.jdbc.Driver");
Connection con =
DriverManager.getConnection("jdbc:mysql://localhost:3306/mycollege","root","password");
Statement stm = con.createStatement();
String qry = "select * from Emp where empid=" + eid;
ResultSet rs = stm.executeQuery(qry);

while(rs.next())
{
id.setText(Integer.toString(rs.getInt(1)));
nm.setText(rs.getString(2));
ds.setText(rs.getString(3));
nt.setText(rs.getString(4));
yr.setText(Integer.toString(rs.getInt(5)));
sl.setText(Integer.toString(rs.getInt(6)));
}

rs.close();
stm.close();
con.close();
}
}

class Employee
{
void details() throws ClassNotFoundException, SQLException
{
Class.forName("com.mysql.cj.jdbc.Driver");
Connection con =
DriverManager.getConnection("jdbc:mysql://localhost:3306/mycollege","root","password");
Statement stm = con.createStatement();
Scanner sc = new Scanner(System.in);
String qry = "select * from Emp order by salary desc";
ResultSet rs = stm.executeQuery(qry);
System.out.println("Employee details in descending order of salary:\n");

while(rs.next())
{
System.out.println(rs.getInt(1) + "\t" + rs.getString(2) + "\t" + rs.getString(3) + "\t" + rs.getString(4) + "\t" + rs.getInt(5) + "\t" + rs.getInt(6));
}
System.out.println("\nEnter employee ID:");
int empid = sc.nextInt();
EmployeeGUI e = new EmployeeGUI(empid);
System.out.println("\nEnter nationality:");
sc.nextLine();
String nat = sc.nextLine();
System.out.println("Enter designation:");
String des = sc.nextLine();
qry = "select * from Emp where nation='" + nat + "' and desig='" + des + "'";
rs = stm.executeQuery(qry);
System.out.println("\nEmployee details for " + nat + "s in " + des + ":\n");

while(rs.next())
{
System.out.println(rs.getInt(1) + "\t" + rs.getString(2) + "\t" + rs.getString(3) + "\t" + rs.getString(4) + "\t" + rs.getInt(5) + "\t" + rs.getInt(6));
}

System.out.println("\nEnter year:");
int year = sc.nextInt();

qry = "delete from Emp where year<" + year;
stm.executeUpdate(qry);
System.out.println("\nDeleted employee details for those who joined before " + year);

sc.close();
rs.close();
stm.close();
con.close();
}
}

class empjdbc
{
public static void main(String[] args) throws ClassNotFoundException, SQLException
{
Employee e = new Employee();
e.details();
}
}
