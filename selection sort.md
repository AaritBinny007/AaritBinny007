//selection sort
#include<stdio.h>
void main()
{
    int a[20];int n,i,j,temp;
    printf("\n enter the array size :");
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
    for(i=0;i<n-1;i++)
    {
        int min=i;
        for(j=i+1;j<n;j++)
        {
            if(a[j]<a[min])
            {
                min=j;
            }
        }
        temp=a[i];
        a[i]=a[min];
        a[min]=temp;
    }
    printf("\n the sorted array :");
     for(i=0;i<n;i++)
    {
        printf("%d",a[i]);
    }
}
