//pgm to check pallindrome or not
#include<stdio.h>
void main()
{
int i,count,j;
i=0;
j=0;
count=0;
char st[20],s[20];
printf("Enter a string: ");
scanf("%s",st);
while (st[count]!='\0')
{
count++;
}
while (st[i]!='\0')
{
s[i]=st[count-1];
count--;
i++;
}
while (i>=0)
{
if (s[count]==st[i-1])
j++;
i--;
count++;
}
if (j==(count-1))
printf("It is pallindrome \n");
else
printf("It is not a pallindrome \n");
}
