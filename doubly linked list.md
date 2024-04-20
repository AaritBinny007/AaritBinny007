//doubly linked list operations
#include <stdio.h>
#include <stdlib.h>
struct node
{
int data;
struct node *next;
struct node *prev;
};
struct node *head, *tail, *ptr, *current, *p;
int item;
void insertatbeginning()
{
p = (struct node *)malloc(sizeof(struct
node));
printf("Enter the data:-\n");
scanf("%d", &p->data);
if (head == NULL)
{
p->next = NULL;
p->prev = NULL;
tail = p;
head = p;
}
else
{
p->next = head;
head->prev = p;
p->prev = NULL;
head = p;
}
}

void insertatend()
{
p = (struct node *)malloc(sizeof(struct
node));
printf("Enter the data:-\n");
scanf("%d", &p->data);
if (head == NULL)
{
p->next = NULL;
p->prev = NULL;
tail = p;
head = p;
}
else
{
tail->next = p;
p->next = NULL;
p->prev = tail;
tail = p;
}
}
void insertafternode()
{
if (head == NULL)
{
printf("The linked list is empty. Cannot
insert after a node.\n");
return;
}
p = (struct node *)malloc(sizeof(struct
node));
printf("Enter the data:-\n");
scanf("%d", &p->data);
ptr = head;
printf("Enter the data of node after
which you want to insert:-\n");
scanf("%d", &item);

//Christopher Cleatus
performoperationsondoubly linkedlist
//U2203071

while (ptr != NULL && ptr->data !=
item)
{
ptr = ptr->next;
}
if (ptr == NULL)
{
printf("Node with data %d not
found\n", item);
free(p);
return;
}
p->next = ptr->next;
p->prev = ptr;
if (ptr->next != NULL)
{
ptr->next->prev = p;
}
ptr->next = p;
}

void deletefrombeginning()
{
if (head == NULL)
{
printf("The linked list is empty\n");
}
else if (head->next == NULL)
{
ptr = head;
head = tail = NULL;
free(ptr);
}
else
{
ptr = head;
head = head->next;

head->prev = NULL;
free(ptr);
}
}
void deletefromend()
{
if (head == NULL)
{
printf("The linked list is empty\n");
}
else if (head->next == NULL)
{
ptr = head;
head = tail = NULL;
free(ptr);
}
else
{
ptr = tail;
tail = tail->prev;
tail->next = NULL;
free(ptr);
}
}
void deletespecinode()
{
if (head == NULL)
{
printf("The list is empty\n");
}
else
{
printf("Enter the data of node you want
to delete\n");
scanf("%d", &item);
ptr = head;
while (ptr->data != item && ptr->next
!= NULL)

{
ptr = ptr->next;
}
if (ptr->data == item)
{
ptr->prev->next = ptr->next;
ptr->next->prev = ptr->prev;
free(ptr);
}
else
{
printf("Node not found\n");
}
}
}
void displayForward()
{
current = head;
if (current == NULL)
{
printf("The linked list is empty\n");
}
else
{
printf("The linked list in forward
direction\n");
while (current != NULL)
{
printf("%d ", current->data);
current = current->next;
}
printf("\n");
}
}
void displayBackward()
{
current = tail;
if (current == NULL)

{
printf("The linked list is empty\n");
}
else
{
printf("The linked list in backward
direction\n");
while (current != NULL)
{
printf("%d ", current->data);
current = current->prev;
}
printf("\n");
}
}
void displayMenu()
{
printf("\nMenu:\n");
printf("1. Insert at the beginning\n");
printf("2. Insert at the end\n");
printf("3. Insert after a node\n");
printf("4. Delete from the
beginning\n");
printf("5. Delete from the end\n");
printf("6. Delete a specific node\n");
printf("7. Display in forward
direction\n");
printf("8. Display in backward
direction\n");
printf("9. Exit\n");
printf("Enter your choice: ");
}
int main()
{
int choice;
do
{
displayMenu();

scanf("%d", &choice);
switch (choice) {
case 1:
insertatbeginning();
break;
case 2:
insertatend();
break;
case 3:
insertafternode();
break;
case 4:
deletefrombeginning();
break;
case 5:
deletefromend();
break;
case 6:
deletespecinode();
break;
case 7:
displayForward();
break;
case 8:
displayBackward();
break;
case 9:
printf("Exiting...\n");
break;
default:
printf("Invalid choice\n"); }} while (choice != 0);
return 0;
}
