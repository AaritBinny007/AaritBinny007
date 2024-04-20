
PROGRAM

#include <stdio.h>
void main()
{
	int a[20]={0},b[20]={0},c[50],p=1,q=1,m,n,i,r=1,k=1;
	printf("Enter the number of terms in first polynomial :");
	scanf("%d",&m);
	printf("Enter the number of terms in second polynomial :");
	scanf("%d",&n);
	a[0]=m;
	b[0]=n;
	for(i=1;i<=2*m;i+=2)
	{    
    	printf("Enter the %dth term exponential of first polynomial: ",k);
    	scanf("%d",&a[i]);
    	printf("Enter the %dth term coefficient: ",k);
    	scanf("%d",&a[i+1]);
    	k++;
	}
	for(i=1;i<=2*n;i+=2)
	{    k=1;
    	printf("Enter the %dth term exponential of second polynomial: ",k);
    	scanf("%d",&b[i]);
    	printf("Enter the %dth term coefficient: ",k);
    	scanf("%d",&b[i+1]);
    	k++;
	}
	while(p<=2*m||q<=2*n)
	{
    	if(a[p]==b[q])
    	{
        	c[r]=a[p];
        	c[r+1]=a[p+1]+b[q+1];
        	p+=2;
        	q+=2;
        	r+=2;
    	}
    	if(a[p]>b[q])
    	{
        	c[r]=a[p];
        	c[r+1]=a[p+1];
        	p+=2;
        	r+=2;
    	}
    	if(a[p]<b[q])
    	{
        	c[r]=b[q];
        	c[r+1]=b[q+1];
        	q+=2;
        	r+=2;
    	}
	}
	r--;
	printf("Sum=");
	for(i=1;i<r;i+=2)
	{
    	printf("%dx^%d+",c[i+1],c[i]);
	}
   
}
