#include<stdio.h>
#include<math.h>
struct point
{
int x;
int y;
};
void main()
{
struct point p1,p2,p3,p4;
    int dist1,sum,dist2;
    printf("\n enter the points");
    scanf("%d",&p1.x);
    scanf("%d",&p1.y);
    scanf("%d",&p2.x);
    scanf("%d",&p2.y);
    scanf("%d",&p3.x);
    scanf("%d",&p3.y);
    scanf("%d",&p4.x);
    scanf("%d",&p4.y);
    dist1=sqrt((pow((p2.x-p1.x),2))+(pow((p2.y-p1.y),2)));
    printf("\n THe distance btw first 2 points is %d",dist1);
    dist2=sqrt((pow((p4.x-p3.x),2))+(pow((p4.y-p3.y),2)));
    printf("\n The distance btw last 2 points is %d",dist2);
    sum=dist1+dist2;
    printf(" \n the sum of these two distances is %d",sum);
}
