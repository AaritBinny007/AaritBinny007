//operations on binary search tree
#include<stdio.h>
#include<stdlib.h>
struct tree
{
int x;
struct tree *l;
struct tree *r;
};
struct tree*getnode(int n);
struct tree* insert(struct tree*,struct tree*);
struct tree * deletion(struct tree *p, int k);
struct tree *Min(struct tree *root);
void search(struct tree *root, int k);
void inorder(struct tree*);
void preorder(struct tree *p);
void postorder(struct tree *p);
void main()
{
int ch,key;
struct tree *root,*z;
root=NULL;
while(1)
{
printf("\nMenu: 1.Insertion 2.Deletion
3.Inorder 4.Preorder 5.Postorder
6.Search\nCHOICE:");
scanf("%d",&ch);
if(ch==1)
{
printf("Enter key to be added");
scanf("%d",&key);
z=getnode(key);
root=insert(root,z);
}
if(ch==2)

{
printf("Enter no. to be deleted");
scanf("%d",&key);
root=deletion(root,key);
}
if(ch==3)
{
inorder(root);
}
if(ch==4)
{
preorder(root);
}
if(ch==5)
{
postorder(root);
}
if(ch==6)
{
printf("Enter no. to be searched");
scanf("%d",&key);
search(root,key);
}
}
}
struct tree*getnode(int n)
{
struct tree*new;
new=(struct tree*)malloc(sizeof(struct tree));
new->x=n;
new->l=NULL;
new->r=NULL;
return new;
}
struct tree* insert(struct tree *p,struct tree *q)
{
struct tree *i,*y;
y=NULL;
i=p;
if(p==NULL)

{
p=q;
}
else
{
while(i!=NULL)
{
y=i;
if((q->x)<(i->x))
i=i->l;
else
i=i->r;
}
if((y->x)>(q->x))
y->l=q;
else
y->r=q;
}
return p;
printf("%d",y->x);
}
void preorder(struct tree *p)
{
if(p!=NULL)
{
printf("%d\t",p->x);
preorder(p->l);
preorder(p->r);
}
}
void inorder(struct tree *p)
{
if(p!=NULL)
{
inorder(p->l);
printf("%d\t",p->x);
inorder(p->r);
}
}
void postorder(struct tree *p)

{
if(p!=NULL)
{
postorder(p->l);
postorder(p->r);
printf("%d\t",p->x);
}
}
struct tree * deletion(struct tree *root, int k)
{
if (root == NULL)
{
printf("Tree Empty or Element to be Deleted
doesn't exist\n");
return NULL;
}
if (root -> x < k)
{
root -> r = deletion (root -> r, k);
return root;
}
else if (root -> x> k)
{
root -> l = deletion (root -> l, k);
return root;
}
else
{
if (root -> l == NULL && root -> r ==
NULL){
printf("Element deleted\n");
free (root);
return NULL;
}
else if (root -> l == NULL)
{
struct tree *temp = root -> r;
free (root);
return temp;
}

else if (root -> r == NULL)
{
struct tree *temp = root -> l;
free (root);
return temp;
}
else
{
struct tree *temp = Min(root -> r);
root -> x = temp -> x;
root -> r = deletion (root -> r, temp -> x);
return root;
}
}
}
struct tree *Min(struct tree *root)
{
while (root -> l!= NULL){
root = root -> l;
}
return root;
}
void search(struct tree *root, int k)
{
if (root == NULL)
printf("Number does not exist in Tree\n");
else if (root -> x == k)
printf("Data %d found\n", root -> x);
else if (root -> x> k)
search(root -> l, k);
else if (root -> x < k)
search(root -> r, k);
}
