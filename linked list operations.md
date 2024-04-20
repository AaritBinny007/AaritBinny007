/*LINKED LIST OPERATIONS
1.INSERT FROM BEGINNING
2.INSERT FROM END
3.INSERT AT SPECIFIED NODE
4.DELETE FROM FRONT
5.DELETE FROM END
6.DELETE AT SPECIFIED NODE
7.DISPLAY*/

#include<stdio.h>
#include<stdlib.h>
struct node
{
    int data;
    struct node*link;
};

struct node*head=NULL;
void insertbegg();
void insertend();
void insertspec();
struct node* createnode();
int length();
void display();
void deletebegg();
void deleteend();
void deletespec();

void main()
{
    int ch;
    printf("\n-------MENU-------");
    printf("\n1.insert at beginning");
    printf("\n2.insert at end");
    printf("\n3.insert at specified");
    printf("\n4.delete at front");
    printf("\n5.delete at end");
    printf("\n6.delete at specified");
    printf("\n7.Display");
    printf("\n8.exit");
    
    while (1) {
        printf("\nSelect a choice from the menu: ");
        scanf("%d", &ch);

        switch (ch)
        {
            case 1:
                insertbegg();
                break;
            case 2:
                insertend();
                break;
            case 3:
                insertspec();
                break;
            case 4:
                deletebegg();
                break;
            case 5:
                deleteend();
                break;
            case 6:
                deletespec();
                break;
            case 7:
                display();
                break;
            default:
                printf("\nInvalid choice");
        }
    }
}

struct node* createnode()
{
    struct node*newnode;
    newnode=(struct node*)malloc(sizeof(struct node));
    newnode->link=NULL;
    return newnode;
}

int length()
{
        int count=0;
    struct node*temp;
    temp=head;
    while(temp!=NULL)
    {
        count++;
        temp=temp->link;
    }
    return count;
}

void insertbegg()
{
    struct node*newnode=createnode();
    
    printf("\nenter the value to be inserted :");
    scanf("%d",&newnode->data);
    newnode->link=head;
    head=newnode;
}

void insertend()
{
    struct node*newnode=createnode();
    printf("enter the data :");
    scanf("%d",&newnode->data);
    newnode->link=NULL;
   if (head == NULL)
    {
        head = newnode;
        return;
    }

     struct node*temp = head;
    while (temp->link != NULL)
    {
        temp = temp->link;
    }
    temp->link = newnode;
}

void insertspec()
{
    int len;
    len=length();
    int pos,i=1;
    struct node*temp=head;
    printf("enter the position :");
    scanf("%d",&pos);
    if(pos>len)
    {
        printf("invalid position");
    }
    else
    {
        temp=head;
        while(i<pos)
        {
            temp=temp->link;
            i++;
        }
    }
    struct node*newnode=createnode();
    printf("\nenter the data :");
    scanf("%d",&newnode->data);
    newnode->link=temp->link;
    temp->link=newnode;
    
}

void display()
{
    struct node *temp = head;
    printf("\n THE ELEMENTS ARE :");
    while (temp != NULL)
    {
        printf("%d ", temp->data);
        temp = temp->link;
    }
}

void deletebegg()
{
    struct node*temp=head;
    if(head==NULL)
    {
        printf("invalid deletion");
    }
    else
    {
        head=temp->link;
        free(temp);
    }
}

void deleteend()
{
    struct node*temp=head;
    struct node*prev=NULL;
    if(temp==NULL)
    {
        printf("the list is empty");
    }
    else
    {
      while(temp->link!=NULL)
      {
         prev=temp;
         temp=temp->link;
      }
     prev->link=NULL;
     free(temp);
}
}
void deletespec()
{
    int len;
    len=length();
    int pos,i=1;
    struct node*temp=head;
    printf("enter the position :");
    scanf("%d",&pos);
    if(pos>len)
    {
        printf("invalid deletion process");
    }
    else
    {
        struct node*prev=NULL;
        while(i<pos)
        {
            prev=temp;
            temp=temp->link;
            i++;
        }
        prev->link=temp->link;;
        free (temp);
    }
}
