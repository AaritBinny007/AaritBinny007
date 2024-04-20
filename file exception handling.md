import java.io.*;
import java.util.Scanner;
class Prime{
static int Check(int a)
{
int i;
if (a<=1)
{
return 0;
}
for(i=2;i<= (a/2);i++)
{
if (a%i==0)
return 0;
}
return 1;
}

public static void main(String args[])
{
try{
FileInputStream f=new FileInputStream("abc.txt");
InputStreamReader in=new InputStreamReader(f);
BufferedReader br= new BufferedReader(in);
FileOutputStream fo=new FileOutputStream("xyz.txt");
OutputStreamWriter out = new OutputStreamWriter(fo);
BufferedWriter buf= new BufferedWriter(out);
String i;
int num;
while ((i=br.readLine())!=null)
{
num=Integer.parseInt(i);
if (Check(num)==1)
{
buf.write("The number is Prime:"+num+"\n");
}
}
buf.write("Aaron James  Roll No : 3 CSE ALPHA");
br.close();
buf.close();
}catch (IOException e){System.out.println(e);}
}
}
