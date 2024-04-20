//reversing of a linked list
#include<stdio.h>
#include<stdlib.h>

void reverse();
void display();
void insert();
struct node*createnode();

struct node
{
    int data;
    struct node*link;
};
struct node*head=NULL;

int main() {
    int ch;
    
    while (1) {
        printf("\n-----menu------");
        printf("\n 1.insert element");
        printf("\n 2.display element");
        printf("\n 3.reverse the list");
        printf("\n 0.exit");
        printf("\n enter the choice from above menu: ");
        scanf("%d", &ch);

        switch (ch) {
            case 1:
                insert();
                break;

            case 2:
                display();
                break;

            case 3:
                reverse();
                break;

            case 0:
                exit(0);

            default:
                printf("\n you entered wrong choice...");
        }
    }
    return 0;
}
struct node*createnode()
{
    struct node*newnode;
    newnode=(struct node*)malloc(sizeof(struct node));
    newnode->link=NULL;
    return newnode;
}

void insert()
{
    struct node*newnode=createnode();
      printf("\n enter the data to be inserted");
      scanf("%d",&newnode->data);
      newnode->link=head;
      head=newnode;
}

void display()
{
    struct node*temp;
    temp=head;
    printf("\n the elements are :");
    while(temp!=0)
    {
        printf("%d",temp->data);
        temp=temp->link;
    }
}

void reverse()
{
    struct node*prevnode,*currnode,*nextnode;
    prevnode=NULL;
    currnode=head;
    while(nextnode!=NULL)
    {
        nextnode=currnode->link;
        currnode->link=prevnode;
        prevnode=currnode;
        currnode=nextnode;
    }
    head=prevnode;
}
