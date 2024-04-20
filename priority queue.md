#include <stdio.h>
#include<stdlib.h>
#define MAX 5
struct PriorityQ
{
int elements[MAX];
int priorities[MAX];
int size;
};
void initializeQ(struct PriorityQ *queue)
{
queue->size = 0;
}
void insert(struct PriorityQ *queue, int
element, int priority)
{
if (queue->size < MAX)
{
int i = queue->size;
while (i > 0 && priority >
queue->priorities[i - 1])
{
queue->elements[i] =
queue->elements[i - 1];
queue->priorities[i] =
queue->priorities[i - 1];
i--;
}
queue->elements[i] = element;
queue->priorities[i] = priority;
queue->size++;
printf("Element inserted
successfully.\n");
} else
{
printf("Priority Queue is full\n");
}
}
void delete(struct PriorityQ *queue)
{
if (queue->size > 0)
{

printf("Deleted: Element=%d,
Priority=%d\n", queue->elements[0],
queue->priorities[0]);
for (int i = 1; i < queue->size; i++) {
queue->elements[i - 1] =
queue->elements[i];
queue->priorities[i - 1] =
queue->priorities[i];
}
queue->size--;
} else {
printf("Priority Queue is empty\n");
}
}
void display(struct PriorityQ *queue)
{
if (queue->size > 0)
{
printf("Priority Queue:\n");
for (int i = 0; i < queue->size; i++)
{
printf("Element=%d, Priority=%d\n",
queue->elements[i], queue->priorities[i]);
}
} else
{
printf("Priority Queue is empty\n");
}
}
void main()
{
struct PriorityQ priorityQ;
initializeQ(&priorityQ);
int ch,element,priority;
do{
printf("\n1.Insert Element\n2.Delete
Element with Highest
Priority\n3.Display\n4.Exit\n");
printf("Enter your choice: ");
scanf("%d", &ch);
switch (ch)
{
case 1:
printf("Enter the element: ");
scanf("%d", &element);
printf("Enter the priority: ");
scanf("%d", &priority);
insert(&priorityQ, element, priority);

break;
case 2:
delete(&priorityQ);
break;
case 3:
display(&priorityQ);
break;
case 4:
break;
default:
printf("Invalid input!!\n");
}
}while(ch!=4);
}
