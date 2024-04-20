import java.util.Scanner;
class arraysum{
	public static void main(String args[]){
	Scanner S=new Scanner(System.in);
	int[][] a=new int[20][20];
	int[][] b=new int[20][20];
	int[][] c=new int[20][20];
	System.out.println("Enter number of rows Matrix A:");
	int r1=S.nextInt();
	System.out.println("Enter number of columns of Matrix A:");
	int c1=S.nextInt();
	System.out.println("Enter number of rows Matrix B:");
	int r2=S.nextInt();
	System.out.println("Enter number of columns of Matrix B:");
	int c2=S.nextInt();
	if (r1==r2 && c1==c2)
	{
	System.out.println("Enter elements of matrix A:");
	for (int i=0;i<r1;i++)
	{
		for(int j=0;j<c1;j++)
		{
			a[i][j]=S.nextInt();
		}
	}
	System.out.println("Enter elements of matrix B:");
	for (int i=0;i<r2;i++)
	{
		for(int j=0;j<c2;j++)
		{
			b[i][j]=S.nextInt();
		}
	}
	
	for (int i=0;i<r1;i++)
		{
			for(int j=0;j<c1;j++)
			{
				c[i][j]=a[i][j]+b[i][j];
			}
		}
	System.out.println("\nMATRIX-B");
	for (int i=0;i<r1;i++)
		{
		for(int j=0;j<c1;j++)
			{
				System.out.print(+a[i][j]);
				System.out.print("\t");
			}
			System.out.println("\n");
		}
	System.out.println("\nMATRIX-B");	
	for (int i=0;i<r1;i++)
		{
		for(int j=0;j<c1;j++)
			{
				System.out.print(+b[i][j]);
				System.out.print("\t");
			}
			System.out.println("\n");
		}
	System.out.println("\nSum of two matrices");
	for (int i=0;i<r1;i++)
		{
		for(int j=0;j<c1;j++)
			{
				System.out.print(+c[i][j]);
				System.out.print("\t");
			}
			System.out.println("\n");
		}
	System.out.println("\nTranspose of the resultant matrix");
	for (int i=0;i<c1;i++)
		{	
			for(int j=0;j<r1;j++)
			{
				System.out.print(+c[j][i]);
				System.out.print("\t");
			}
			System.out.println("\n");
		}
	}
	else
		System.out.println("Addition not possible!");
	
}}
