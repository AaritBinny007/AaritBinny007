#include<stdio.h>
int partition(int a[], int start, int end);
void quicksort(int a[], int start, int end);
int main() {
int i, n, a[20];
printf("Enter the size of array: ");
scanf("%d", &n);
for (i = 0; i < n; i++) {
printf("Enter the element: ");
scanf("%d", &a[i]);
}
printf("Original Array: ");
for (i = 0; i < n; i++) {
printf("%d\t", a[i]);
}
quicksort(a, 0, n - 1);
printf("\nSorted Array: ");
for (i = 0; i < n; i++) {
printf("%d\t", a[i]);
}
return 0;
}
void quicksort(int a[], int start, int end) {
int p;
if (start < end) {
p = partition(a, start, end);
printf("\nIteration: ");
for (int i = start; i <= end; i++) {
printf("%d\t", a[i]);
}
quicksort(a, start, p - 1);
quicksort(a, p + 1, end);
}
}
int partition(int a[], int start, int end) {
int pivot, temp;

int low, high, l, u;
low = start;
high = end;
pivot = a[low];
l = low + 1;
u = high;
while (u >= l) {
while (a[l] <= pivot && l <= high) {
l = l + 1;
}
while (a[u] >= pivot && u > low) {
u = u - 1;
}
if (u > l) {
temp = a[l];
a[l] = a[u];
a[u] = temp;
}
}
temp = a[u];
a[u] = a[low];
a[low] = temp;
return u;
}
