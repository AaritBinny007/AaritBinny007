#include <stdio.h>
#include <stdlib.h>
#define MAX 10
struct Node
{
int vertex;
struct Node* link;
};
struct Node* graph[MAX];
int visited[MAX];
void insert(int vertex);
void dfs(int v);
void bfs(int start_vertex);
void dis_adj_list();
void dis_adj_matrix();
void dfs_traversal(int v);
void bfs_traversal(int start_vertex);
void main()
{
int ch, x, s, dis;
do {
printf("\n1.Insertion\n2.Searching\n3.Displa
y\n4.Exit\n");
printf("\nEnter your choice:");
scanf("%d", &ch);
switch (ch)
{
case 1:
printf("\nEnter the element to

be inserted:");

scanf("%d", &x);
insert(x);
break;

case 2:
do{
printf("\n1.DFS(Depth First

Search)\n2.BFS(Breadth First
Search)\n3.Exit from searching menu\n");
printf("\nEnter the type of

search you need:");

scanf("%d", &s);
switch (s)
{
case 1:
printf("\nEnter the starting

vertex for DFS:");

scanf("%d", &x);
dfs(x);
break;
case 2:
printf("\nEnter the starting

vertex for BFS:");

scanf("%d", &x);
bfs(x);
break;
case 3:
break;
default:
printf("\nInvalid option!!\n");
break;
}
}while(s!=3);
break;
case 3:
do {
printf("\n1.Represent by
Adjacency Matrix\n2.Represent by
Adjacency List\n3.Exit from the display
menu\n");

printf("\nEnter the type of

representation you needed:");
scanf("%d", &dis);
switch (dis)

{
case 1:
dis_adj_matrix();
break;
case 2:
dis_adj_list();
break;
case 3:
break;
default:
printf("\nInvalid

choice!!\n");

break;
}
} while (dis != 3);
break;
case 4:
break;
default:
printf("\nInvalid option!!\n");
break;
}
}while(ch!=4);
}
void insert(int vertex)
{
struct Node* newNode = (struct
Node*)malloc(sizeof(struct Node));
newNode->vertex = vertex;
newNode->link = NULL;
if (!graph[vertex]) {
graph[vertex] = newNode;
} else {
struct Node* temp = graph[vertex];
while (temp->link != NULL) {
temp = temp->link;
}
temp->link = newNode;
}

printf("\nElement inserted
successfully\n");
}
void dfs(int v)
{
printf("\nDFS starting from vertex
%d:\n", v);
for (int i = 0; i < MAX; i++)
{
visited[i] = 0;
}
dfs_traversal(v);
printf("\n");
}
void dfs_traversal(int v) {
struct Node* w = graph[v];
visited[v] = 1;
printf("%d ", v);
while (w != NULL) {
if (!visited[w->vertex]) {
dfs_traversal(w->vertex);
}
w = w->link;
}
}
void bfs(int start_vertex) {
printf("\nBFS starting from vertex
%d:\n", start_vertex);
for (int i = 0; i < MAX; i++) {
visited[i] = 0;
}
bfs_traversal(start_vertex);
printf("\n");
}
void dis_adj_list()
{
int i;
struct Node* temp;

for (i = 0; i < MAX; i++)
{
printf("\n%d:", i);
temp = graph[i];
while (temp != NULL)
{
printf(" %d", temp->vertex);
temp = temp->link;
}
}
printf("\n");
}
void dis_adj_matrix()
{
int i, j;
printf("\nAdjacency Matrix:\n");
for (i = 0; i < MAX; i++) {
for (j = 0; j < MAX; j++)
{
if (graph[i] != NULL)
{
struct Node* temp = graph[i];
int found = 0;
while (temp != NULL)
{
if (temp->vertex == j)
{
found = 1;
break;
}
temp = temp->link;
}
printf("%d ", found);
} else
{
printf("0 ");

}
}
printf("\n");
}
}
void bfs_traversal(int start_vertex) {
int queue[MAX];
int front = -1, rear = -1;
queue[++rear] = start_vertex;
visited[start_vertex] = 1;
while (front != rear) {
int current_vertex = queue[++front];
printf("%d ", current_vertex);
struct Node* w =
graph[current_vertex];
while (w != NULL) {
if (!visited[w->vertex]) {
queue[++rear] = w->vertex;
visited[w->vertex] = 1;
}
w = w->link;
}
}
}
