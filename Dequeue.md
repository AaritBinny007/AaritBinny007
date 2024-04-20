//a. Insert from the front
//b. Insert from rear
//c. Delete from front
//d. Delete from rear
//e. Display

PROGRAM

# include<stdio.h>
void main()
{
	int i,j,ch,n,a[30],front=-1,rear=-1,v,f;
	printf("\nEnter The capacity of Queue");
	scanf("%d",&n);
	i=1;
	while(i!=0)
	{
    	printf("1.Front insertion  \n2.Rear Insertion  \n3.Front Deletion  \n4.Rear Deletion  \n5.Display  \n6.Exit \nEnter the option : ");
    	scanf("%d",&ch);
    	if(ch==1)
    	{
        	if(v==n)
        	{
            	printf("The Queue is Full\n");
        	}
        	else if(front==-1)
        	{
            	front=0;
            	rear=0;
            	printf("Enter the element:\n");
            	scanf("%d",&a[front]);
            	v++;
            	front=n-1;
        	}
        	else if(front==0)
        	{
            	front=n-1;
            	printf("Enter the element:\n");
            	scanf("%d",&a[front]);
            	front--;
            	v++;
        	}
        	else
        	{
            	printf("\nEnter The Elements\n");
            	scanf("%d",&a[front]);
            	v++;
            	front--;
        	}
    	}
    	else if (ch==2)
    	{
        	if(v==n)
        	{
            	printf("\nQueue is Full\n");
        	}
        	else
        	{
            	rear=(rear+1)%n;
            	printf("\nEnter the elemnts:\n");
            	scanf("%d",&a[rear]);
            	v++;
        	}
  	 
    	}
    	else if (ch==3)
    	{
        	if(v==0 || front==-1 && rear==-1)
        	{
            	printf("\nQueue is empty\n");
        	}
        	else if(front==rear && v==1)
        	{
            	printf("%d is deleted\n",a[front]);
            	front=-1;
            	rear=-1;
            	v--;
        	}
        	else
        	{
            	front=(front+1)%n;
            	printf("%d is deleted\n",a[front]);
            	v--;
        	}
    	}
    	else if (ch==4)
    	{
        	if(v==0 ||front==-1 && rear==-1)
        	{
            	printf("\n Queue Is Empty\n");
        	}
        	else if(rear==0)
        	{
            	printf("\n Deleted Element %d\n",a[rear]);
            	rear=n-1;
            	v--;
        	}
        	else if(front==rear && v==1)
        	{
            	printf("Deleted Element %d\n",a[front]);
            	front=-1;
            	rear=-1;
            	v--;
        	}
        	else
        	{
            	printf("Deleted Element %d\n",a[rear]);
            	rear--;
            	v--;
        	}
    	}
    	else if (ch==5)
    	{
        	f=(front+1)%n;
        	j=0;
        	while(j<v)
        	{
            	printf("%d",a[f]);
            	f=(f+1)%n;
            	j++;
        	}
    	}
        	else if (ch==6)
        	{
            	i=0;
        	}
        	else
        	{
            	printf("\nInvalid Choice");
        	}
	}
}
