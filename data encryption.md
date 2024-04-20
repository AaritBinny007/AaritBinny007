import java.io.*;
import java.util.Scanner;
class Encryption{
    public static void main(String args[]){
        try {
            FileInputStream in = new FileInputStream("data.txt");
            FileOutputStream out = new FileOutputStream("encry.txt");
            int i;
            Scanner scan = new Scanner(System.in);
            System.out.print("Enter key: ");
            int key = scan.nextInt();
            while ((i = in.read()) != -1)
                out.write(i+key);
            System.out.println("Data Encrypted!");
            System.out.println("Aaron James Roll Number 3 CSEALPHA");
            in.close();
            out.close();
        }catch(Exception e){System.out.println(e);}
    }
}
