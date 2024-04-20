#include <stdio.h>
struct employ
{
    char name[10];
    int employid;
    int sal;
};
void main()
{
    struct employ e[10];
    int n,i;
    printf("\n enter n");
    scanf("%d",&n);
    printf("\n enter the name,id,sal of employees one by one respectively \n");
    for(i=0;i<n;i++)
    {
       scanf("\n %s \t %d \t %d",e[i].name,&e[i].employid,&e[i].sal);
    }
    for(i=0;i<n;i++)
    {
       printf("\n %s \t %d \t %d",e[i].name,e[i].employid,e[i].sal);
    }
 }
