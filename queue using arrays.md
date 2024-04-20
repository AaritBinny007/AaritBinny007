//stack implementation using array
/*1.push
2.pop
3.peak value
4.display
*/

#include<stdio.h>
#include<stdlib.h>

struct stack
{
    int stack[20];
    int top;
};

void push();
void pop();
void peak();
void display();

int n;
struct stack s;

void main()
{
    int ch;
    printf("\n------menu------");
    printf("\n 1.push");
    printf("\n 2.pop");
    printf("\n 3.display");
    printf("\n 4.peak element");
    printf("\n 0.exit");
    printf("\n enter the size of the stack :");
    scanf("%d",&n);
    
    s.top=-1;
    
    
    while(1)
    {
        printf("\n enter the choice from above menu :");
        scanf("%d",&ch);
        switch(ch)
        {
            case 1:
                 push();
                 break;
                 
            case 2:
                 pop();
                 break;
                 
            case 3:
                 display();
                 break;
                 
            case 4:
                 peak();
                 break;
                 
            case 0:
                 exit(0);
                 
            default :
                 printf("\n wrong choice...please try again");
        }
    }
}



void push()
{
    
    int data;
    if(s.top==n-1)
    {
        printf("\n stack is overflow ");
    }
    else
    {
        s.top++;
        printf("\n enter the data :");
        scanf("%d",&data);
        s.stack[s.top]=data;
    }
}

void pop()
{
    int item;
    if(s.top==-1)
    {
        printf("\n the stack is underflow ");
    }
    else
    {
        item=s.stack[s.top];
        s.top--;
    }
}

void display()
{
    int i;
    printf("\n the stack is :");
   for(i=0;i<=s.top;i++)
   {
       printf("%d",s.stack[i]);
   }
}

void peak()
{
{
    if(s.top != -1)
    {
        printf("\n the peak element is: %d", s.stack[s.top]);
    }
    else
    {
        printf("\n the stack is empty");
    }
}
}
