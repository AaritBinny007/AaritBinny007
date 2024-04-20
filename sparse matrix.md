#include <stdio.h>
void main()
{
	int a[10][10], b[10][10], r1, c1, r2, c2, a1[10][10], f1[10][10], d1[10][10], e1[10][10];
	int b1[10][10], i, j, p = 1, count = 0, countb = 0;

	printf("enter row1:");
	scanf("%d", &r1);
	printf("enter column1:");
	scanf("%d", &c1);
	printf("enter row2:");
	scanf("%d", &r2);
	printf("enter column2:");
	scanf("%d", &c2);
	if ((r1 == r2) && (c1 == c2))
	{
	printf("enter elements of 1:\n");
	for (i = 0; i < r1; i++)
	{
    	for (j = 0; j < c1; j++)
    	{
        	scanf("%d", &a[i][j]);
    	}
	}
	printf("enter elements of 2:\n");
	for (i = 0; i < r2; i++)
	{
    	for (j = 0; j < c2; j++)
    	{
        	scanf("%d", &b[i][j]);
    	}
	}
	for (i = 0; i < r1; i++)
	{
    	for (j = 0; j < c1; j++)
    	{
        	if (a[i][j] != 0)
        	{
            	count++;
        	}
        	if (b[i][j] != 0)
        	{
            	countb++;
        	}
    	}
	}
	a1[0][0] = r1;
	a1[0][1] = c1;
	a1[0][2] = count;
	b1[0][0] = r2;
	b1[0][1] = c2;
	b1[0][2] = countb;
	for (i = 0; i < r2; i++)
	{
    	for (j = 0; j < c2; j++)
    	{
        	if (a[i][j] != 0)
        	{
            	a1[p][0] = i;
            	a1[p][1] = j;
            	a1[p][2] = a[i][j];
            	p++;
        	}
    	}
	}
	p = 1;
	for (i = 0; i < r1; i++)
	{
    	for (j = 0; j < c1; j++)
    	{
        	if (b[i][j] != 0)
        	{
            	b1[p][0] = i;
            	b1[p][1] = j;
            	b1[p][2] = b[i][j];
            	p++;
        	}
    	}
	}
	printf("sparse of 1:");
	printf("\n");
	for (i = 0; i <= count; i++)
	{
    	for (j = 0; j < 3; j++)
    	{
        	printf("%d", a1[i][j]);
        	printf("\t");
    	}
    	printf("\n");
	}
	printf("\n");
	printf("sparse of 2:");
	printf("\n");
	for (i = 0; i <= countb; i++)
	{
    	for (j = 0; j < 3; j++)
    	{
        	printf("%d", b1[i][j]);
        	printf("\t");
    	}
    	printf("\n");
	}
	printf("\n");
	printf("transpose of 1: \n");
	f1[0][0] = c1;
	f1[0][1] = r1;
	f1[0][2] = count;
	p = 1;
	int col;

	for (col = 0; col < c1; col++)
	{
    	for (i = 1; i <= count; i++)
    	{
        	if (a1[i][1] == col)
        	{
            	f1[p][0] = a1[i][1];
            	f1[p][1] = a1[i][0];
            	f1[p][2] = a1[i][2];
            	p++;
        	}}}
	for (i = 0; i <= count; i++)
	{
    	for (j = 0; j < 3; j++)
    	{
        	printf("%d", f1[i][j]);
        	printf("\t");
    	}
    	printf("\n");
	}
    
  	// transpose2
	printf("\n");
	printf("transpose of 2: \n");
	e1[0][0] = c1;
	e1[0][1] = r1;
	e1[0][2] = countb;
	p = 1;

	for (col = 0; col < c2; col++)
	{
    	for (i = 1; i <= countb; i++)
    	{
        	if (a1[i][1] == col)
        	{
            	e1[p][0] = a1[i][1];
            	e1[p][1] = a1[i][0];
            	e1[p][2] = a1[i][2];
            	p++;
        	}}}
	for (i = 0; i <= countb; i++)
	{
    	for (j = 0; j < 3; j++)
    	{
        	printf("%d", e1[i][j]);
        	printf("\t");
    	}
    	printf("\n");
	}

	d1[0][0] = a1[0][0];
	d1[0][1] = a1[0][1];
	printf("\nSparse matrix addition \n");
	int m = 1, n = 1, k = 1;
	for (int i = 0; i < count; i++)
	{
    	for (j = 0; j < c1; j++)
    	{
        	if ((a1[m][0] == i && a1[m][1] == j) && (b1[n][0] == i && b1[n][1] == j))
        	{
            	d1[k][0] = a1[m][0];
            	d1[k][1] = a1[m][1];
            	d1[k][2] = a1[m][2] + b1[n][2];
            	m++;
            	k++;
            	n++;
        	}
        	else if ((b1[n][0] == i) && (b1[n][1] == j))
        	{
            	d1[k][0] = b1[n][0];
            	d1[k][1] = b1[n][1];
            	d1[k][2] = b1[n][2];
            	n++;
            	k++;
        	}
        	else if ((a1[m][0] == i) && (a1[m][1] == j))
        	{
            	d1[k][0] = a1[m][0];
            	d1[k][1] = a1[m][1];
            	d1[k][2] = a1[m][2];
            	m++;
            	k++;
        	}}}
	d1[0][2] = count;
	for (i = 0; i <= count; i++)
	{
    	for (j = 0; j < 3; j++)
    	{
        	printf("%d \t", d1[i][j]);
    	}
    	printf("\n");
	}}
	else
	{    printf("Matrix addition is not possible\n");
   	 
	}}
