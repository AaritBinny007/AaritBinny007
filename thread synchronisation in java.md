import java.util.Scanner;
class Display{
 public synchronized void display(int num){
  System.out.println(num);
  try{
    Thread.sleep(1500);
    }catch(InterruptedException e){System.out.println(e);}
    System.out.println(num);
    }
    }
   
    class OddThread extends Thread{
    Display d;
     
    OddThread(Display display){
    d=display;
     }
       
     public void run(){
     for(int i=1;i<=num;i+=2){
     d.display(i);
     }
     }
     }
         
     class EvenThread extends Thread{
     Display d;
     
     EvenThread(Display display){
     d=display;
     }
     
     public void run(){
     for(int i=2;i<=num;i+=2){
     d.display(i);
     }
     }
      }
     
class Oddeven{
      public static void main(String args[]){
      Scanner s=new Scanner(System.in);
      System.out.println("Enter number: ");
      int num=s.nextInt();
      Display d=new Display(num);
      OddThread ot=new OddThread(d);
      EvenThread et=new EvenThread(d);
      ot.start();
      et.start();
      }
      }
