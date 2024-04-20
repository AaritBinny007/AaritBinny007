//merge sort by Aarit
#include <stdio.h>
#include <stdlib.h>
void inser(int a[],int n);
void mergesort(int a[],int l,int h);
void merge(int a[],int l,int mid,int h);
void display(int a[],int n);
void main()
{ int ch,n;
int l=0;
int g[100];
int a[100];
printf("enter the size");
scanf("%d",&n);
int h=n-1;
do
{
printf("\n1:Insert 2:Merge sort 3:display
4:Exit");
printf("\nenter choice ");
scanf("%d",&ch);
switch(ch)
{
case 1:
inser(a,n);
break;
case 2:
mergesort(a,l,h);
break;
case 3:
display(a,n);
break;

case 4:
printf("Exiting..");
break;
default:
printf("Invalid");
break;
}
}while(ch!=4);
}
void inser(int a[],int n)
{
int i;
printf("enter the elements");
for(i=0;i<n;i++)
{
scanf("%d",&a[i]);
}

}
void display(int a[],int n)
{
int i;
printf("sorted :");
for(i=0;i<n;i++)
{
printf("%d \t",a[i]);
}
}
void mergesort(int a[],int l,int h)
{ int mid;
if(l<h)
{
mid=(l+h)/2;
mergesort(a,l,mid);
mergesort(a,mid+1,h);
merge(a,l,mid,h);
}

implementMergesort
//Christopher Cleatus
//U2203071

}
void merge(int a[],int l,int mid,int h)
{
int i=l,j=mid+1,k=0;
int b[50];
while(i<=mid&&j<=h)
{
if(a[i]<=a[j])
{
b[k]=a[i];
i++;
}
else
{
b[k]=a[j];
j++;
}
k++;
}
while(i<=mid)
{
b[k]=a[i];
i++;
k++;
}
while(j<=h)
{
b[k]=a[j];
j++;
k++;
}
for(i=l,k=0;i<=h;i++,k++)
a[i]=b[k];
}
