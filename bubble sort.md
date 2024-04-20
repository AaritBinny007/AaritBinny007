1. //bubble sort
#include<stdio.h>
void main()
{
    int a[10];int i,j,n,k,temp;
    printf("\n enter the size of the array :");
    scanf("%d",&n);
    printf("\n enter the array elements :");
    for(i=0;i<n;i++)
    {
        scanf("%d",&a[i]);
    }
    printf("\n the array elements before sorting :");
     for(i=0;i<n;i++)
    {
        printf("%d",a[i]);
    }
    for(i=0;i<n;i++)
    {
        for(j=0;j<n-1-i;j++)
        {
            temp=a[j];
            a[j]=a[j+1];
            a[j+1]=temp;
        }
        for(k=0;k<n;k++)
        {
            printf("%d",a[k]);
        }
        printf("\n");
    }
     printf("\n the array elements after sorting :");
        for(i=0;i<n;i++)
        {
            printf("%d",a[i]);
        }
}
