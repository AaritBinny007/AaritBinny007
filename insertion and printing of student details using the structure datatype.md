#include <stdio.h>
struct student
{
int r;
char name[15];
int mark;
};
void main()
{
struct student c[50];
int i,n,q;
printf ("Enter the Number of Students\n");
scanf ("%d",&n);
for (i=0;i<n;i++)
{
printf ("Details of Student %d:\n",i+1);
printf ("Enter the RollNo:");
scanf("%d",&c[i].r);
printf ("Enter the student Name:");
scanf("%s",c[i].name);
printf ("Enter the student Marks:");
scanf("%d",&c[i].mark);
printf ("\n");
}
for(i=0;i<n;i++)
{
printf ("Details of Student %d:\n",i+1);
printf ("student RollNo : %d\n",c[i].r);
printf ("student Name : %s\n",c[i].name);
printf ("Enter the student Marks : %d\n",c[i].mark);
}
}
