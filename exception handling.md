import java.io.*;

import java.util.Scanner;

public class SBIATM {

public static void main(String[] args) {

Scanner s = new Scanner(System.in);

System.out.print("Enter your account number: ");

String accno = s.next();

double balance = 0;


try {

balance = readAccountBalance(accno);

System.out.println("Available balance: " + balance);

System.out.print("Choose an operation (1 - Withdraw, 2 - Deposit, 3 - Transfer): ");

int ch = s.nextInt();

switch (ch) {

case 1:

System.out.print("Enter withdrawal amount: ");

double withdraw = s.nextDouble();

if (withdraw > balance) {

throw new InsufficientBalanceException("Insufficient balance");

}

balance -= withdraw;

break;

case 2:

System.out.print("Enter deposit amount: ");

double deposit = s.nextDouble();

balance += deposit;

break;

case 3:

System.out.print("Enter transfer amount: ");

double transfer = s.nextDouble();

if (transfer > balance) {

throw new InsufficientBalanceException("Insufficient balance");

}

System.out.print("Enter recipient's account number: ");

String recipientAccno = s.next();

double recipientBalance = readAccountBalance(recipientAccno);

recipientBalance += transfer;

writeAccountBalance(recipientAccno, recipientBalance);

balance -= transfer;

break;

default:

System.out.println("Invalid choice");

}

writeAccountBalance(accno, balance);

} catch (IOException e) {

System.out.println("Error accessing the file: " + e.getMessage());

} catch (InsufficientBalanceException e) {

System.out.println(e.getMessage());

} finally {

System.out.println("Available balance: " + balance);

} }


private static double readAccountBalance(String accno) throws IOException {

File f = new File(accno + ".txt");

 if (!f.exists()) {

     throw new FileNotFoundException("Account not found");

        }

BufferedReader br = new BufferedReader(new FileReader(f));

String balanceString = br.readLine();

br.close();

return Double.parseDouble(balanceString);

    }


private static void writeAccountBalance(String accno, double balance) throws IOException {

File f = new File(accno + ".txt");

BufferedWriter bw = new BufferedWriter(new FileWriter(f));

bw.write(String.valueOf(balance));

        bw.close();

    }

}


class InsufficientBalanceException extends Exception {

    public InsufficientBalanceException(String message) {

        super(message);

    }

}
