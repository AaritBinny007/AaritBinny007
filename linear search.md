
//linear search 
#include<stdio.h>
void main()
{
    int a[20];int i,tar,s; int flag=0;
    printf("\nenter the size of the array");
    scanf("%d",&s);
    printf("\nenter the array elements :");
    for(i=0;i<s;i++)
    {
        scanf("%d",&a[i]);
    }
    printf("\nthe array elements are :");
    for(i=0;i<s;i++)
    {
        printf("%d",a[i]);
    }
    printf("\nenter the target element :");
    scanf("%d",&tar);
    for(i=0;i<s;i++)
    {
        if(a[i]==tar)
        {
            flag=1;
            break;
        }
      
    }
    if(flag)
    {
        printf("element found at %d",i);
    }
    else
    {
        printf("element not found");
    }
}
