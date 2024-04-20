#include<stdio.h>
struct complex
{
 int real;
 int img;
 }c1,c2;
 void add(struct complex,struct complex);
void main()
{
 printf("enter the real and imaginary part ");
 scanf("%d%d",&c1.real,&c1.img);
 printf("enetr second no real and imaginary part");
 scanf("%d%d",&c2.real,&c2.img);
 add(c1,c2);
 }
 void add(struct complex c1,struct complex c2)
 {
 struct complex c3;
 c3.real=c1.real+c2.real;
 c3.img=c1.img+c2.img;
 printf("%d+%di",c3.real,c3.img);
 }
