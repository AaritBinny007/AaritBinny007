//program to implement has table and collision techniques
#include <stdio.h>
#include <stdlib.h>
struct hashtable
{
int *l;
int *q;
};
void hash(int[], int, struct hashtable *);
void get(int, int, int, struct hashtable *);
void delete(int, int, int, struct hashtable *);
int main()
{
int n, i, ch, x, j, op;
struct hashtable table;
printf("Enter the limit of keys: ");
scanf("%d", &n);
table.l = (int *)malloc(n * sizeof(int));
table.q = (int *)malloc(n * sizeof(int));
for (i = 0; i < n; i++)
{
printf("Enter the %d key: ", i + 1);
scanf("%d", &table.l[i]);
}
hash(table.l, n, &table);
do {
printf("\n1. Linear probing\n2.
Quadratic probing\n3. Exit");
printf("\nEnter the collision technique:
");
scanf("%d", &ch);
switch (ch)
{
case 1:
do {
printf("\n1. Searching\n2.
Delete\n3. Exit linear probing\n");
printf("Enter your choice: ");
scanf("%d", &op);
switch(op)
{
case 1:
printf("Enter the key to

search:");

scanf("%d", &x);
get(x, 1, n, &table);
break;
case 2:
printf("Enter the key to delete:

");

scanf("%d", &x);
delete(x, 1, n, &table);
break;
case 3:
break;
default:
printf("Wrong input\n");
break;
}
} while (op != 3);
break;
case 2:
do {
printf("\n1. Searching\n2.
Delete\n3. Exit quadratic probing");
printf("\nEnter the option: ");
scanf("%d", &op);
switch (op) {
case 1:
printf("Enter the key to

search:");

scanf("%d", &x);
get(x, 2, n, &table);
break;
case 2:
printf("Enter the key to delete:

");

scanf("%d", &x);
delete(x, 2, n, &table);
break;
case 3:
break;
default:
printf("Wrong input\n");
break;
}
} while(op != 3);
break;
case 3:
break;

default:
printf("Wrong input\n");
break;
}
} while (ch != 3);
free(table.l);
free(table.q);
return 0;
}
void delete(int x, int d, int n, struct hashtable
*a)
{
int k, key, j;
if (d == 1)
{
key = x % n;
k = 1;
j = 0;
while (k != 0 && j < n)
{
if (a->l[key] == x)
{
printf("Element deleted at %d", key);
a->l[key] = 0;
k = 0;
break;
} else
{
j++;
key = (key + j) % n;
}
}
} else if (d == 2)
{
key = x % n;
k = 1;
j = 0;
while (k != 0 && j < n)
{
if (a->q[key] == x)
{
printf("Element deleted at %d", key);
a->q[key] = 0;
k = 0;
break;
} else
{

j++;
key = (key + j * j) % n;
}
}
}
}
void get(int x, int d, int n, struct hashtable *a)
{
int k, key, j;
if (d == 1)
{
key = x % n;
k = 1;
j = 0;
while (k != 0 && j < n)
{
if (a->l[key] == x) {
printf("Element found at %d", key);
k = 0;
break;
} else {
j++;
key = (key + j) % n;
}
}
if (k != 0) {
printf("Element not found\n");
}
} else if (d == 2) {
key = x % n;
k = 1;
j = 0;
while (k != 0 && j < n) {
if (a->q[key] == x) {
printf("Element found at %d", key);
k = 0;
break;
} else {
j++;
key = (key + j * j) % n;
}
}
if (k != 0) {
printf("Element not found\n");
}
}
}
void hash(int b[50], int n, struct hashtable *a)

{
int i, j = 0, x, key, k = 1, e = 1;
for (i = 0; i < n; i++) {
x = b[i];
k = 1;
j = 0;
key = x % n;
while (k != 0 && j < n) {
if (a->l[key] == 0) {
a->l[key] = x;
k = 0;
break;
} else {
j++;
key = (key + j) % n;
}
}
e = 1;
j = 0;
key = x % n;
while (e != 0 && j < n) {
if (a->q[key] == 0) {
a->q[key] = x;
e = 0;
} else {
j++;
key = (key + j * j) % n;
}
}
}
}
