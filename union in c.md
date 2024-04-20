#include<stdio.h>
#include<string.h>
#define C_SIZE 50
union address
{
char name[C_SIZE];
char house[C_SIZE];
char cname[C_SIZE];
char state[C_SIZE];
int pincode;
};
void main()
{
union address a1;
printf("\n Enter Name:");
scanf("%s",a1.name);
printf("\n Enter house name:");
scanf("%s",a1.house);
printf("\n Enter city name:");
scanf("%s",a1.cname);
printf("\n Enter state:");
scanf("%s",a1.state);
printf("\n Enter pincode:");
scanf("%d",&a1.pincode);
printf("Values are\n");
printf("Name:%s\n",a1.name);
printf("House name:%s\n",a1.house);
printf("City:%s\n",a1.cname);
printf("State:%s\n",a1.state);
printf("Name:%d\n",a1.pincode);
}
