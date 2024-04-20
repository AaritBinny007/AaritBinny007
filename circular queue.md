//c program for circular queue 
//perform the following as menu driven
// a.insertion
// b.deletion
// c.display
// d.isempty
// e.isfull
// f.exit
#include<stdio.h>
void enqueue(int,int);
int dequeue();
void isfull();
void isempty();
void display();
struct queue
{
    int front;
    int rear;
    int q[50];
}q1;
void main()
{
    struct queue;
    int ch,n,a;
    q1.front=q1.rear=-1;
    printf("Enter the size of queue: ");
    scanf("%d",&n);
    do
    {
        printf("***Menu***\n");
        printf("1.Insert\n2.Delete\n3.Isfull\n4.Isempty\n5.Display\n6.Exit\n");
        printf("Enter choice: ");
        scanf("%d",&ch);
        if(ch==1)
        {
            printf("Enter element to be inserted: ");
            scanf("%d",&a);
            enqueue(a,n);
        }
        else if(ch==2)
        {
            dequeue(n);
        }
        else if(ch==3)
        {
            isfull(n);
        }
        else if(ch==4)
        {
            isempty();
        }
        else if(ch==5)
        {
            display(n);
        }
        else if(ch==6)
        {
            break;
        }
        else
        {
            printf("Invalid choice");
        }
    }while(ch!=6);
}
void enqueue(int a,int n)
{
    if(q1.front==(q1.rear+1)%n)
        printf("Queue is full\n");
    else if(q1.front==-1 && q1.rear==-1)
    {
        q1.front=q1.rear=0;
        q1.q[q1.rear]=a;
        printf("Element %d added to queue\n",q1.q[q1.rear]);
    }
    else
    {
        q1.rear=(q1.rear+1)%n;
        q1.q[q1.rear]=a;
        printf("Element %d added to queue\n",q1.q[q1.rear]);
    }
}
int dequeue(int n)
{
   if(q1.front==-1 && q1.rear==-1)
        printf("Queue is empty\n");
    else if(q1.front==q1.rear)
        q1.front=q1.rear=-1;
    else
    {
        printf("Element %d removed from Queue\n",q1.q[q1.front]);
        q1.front=(q1.front+1)%n;
    }
}
void isfull(int n)
{
    if(q1.front==(q1.rear+1)%n)
        printf("Queue is full\n");
    else
        printf("Queue is not full\n");
}
void isempty()
{
    if(q1.front==-1 && q1.rear==-1)
        printf("Queue is Empty\n");
    else
        printf("Queue is not empty\n");
}
void display(int n)
{
    int i=q1.front;
    if(q1.front=-1 && q1.rear==-1)
        printf("Queue is empty\n");
    else
    {
        printf("Elements of queue are: \n");
        while(i!=q1.rear+1)
        {
            printf("%d\t",q1.q[i]);
            i=(i+1)%n;
        }
    }
}
