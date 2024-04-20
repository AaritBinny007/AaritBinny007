
2.//insertion sort operation
#include<stdio.h>
void main()
{
    int a[20];int i,j,temp,n;
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
  for(i=1;i<n;i++)
  {
      j=i-1;
      temp=a[i];
      while(j>=0 && a[j]>temp)
      {
          a[j+1]=a[j];
          j--;
      }
      a[j+1]=temp;
  }
    printf("\n the array elements affter sorting :");
        for(i=0;i<n;i++)
    {
        printf("%d",a[i]);
    }
    printf("\n");
}
