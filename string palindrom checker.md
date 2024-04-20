#include<stdio.h>
void main()
{
char st[20],s[20];
int k,j,count,i;
count=0;
i=0;
j=0;
k=0;
printf("Enter string: ");
scanf("%s",st);
while (st[i]!='\0')
{
count++;
i++;
}
while (i>=0)
{
s[j]=st[i-1];
j++;
i--;
}
while (j>=0)
{
if (s[i]==st[j-1])
{
k++;
}

i++;
j--;
}

if ((k-1)==i)
printf("It is pallindrome\n");

else
printf("It is not pallindrome\n");
}
