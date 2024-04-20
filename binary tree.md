//binary tree
#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;
struct Node
{ int data;
struct Node* left;
struct Node* right;
};
struct Node* createNode(int
data);
struct Node* insert(struct
Node* root, int data);
struct Node*
deleteTree(struct Node*
root);
void inorder(struct Node*
root);
void preorder(struct Node*
root);
void postorder(struct Node*
root);
struct Node* createNode(int
data) {
struct Node* node = (struct
Node*)malloc(sizeof(struct
Node));
node-&gt;data = data;
node-&gt;left = NULL;
node-&gt;right = NULL;
return node;
}
struct Node* insert(struct
Node* root, int data)
{
if (root == NULL) {
return createNode(data);
} if (
root-&gt;left == NULL) {
root-&gt;left =
createNode(data);
}
else if (root-&gt;right ==
NULL) {
root-&gt;right =
createNode(data);
}
else {
root-&gt;left = insert(root-&gt;left,
data);
} return root;

}
struct Node*
deleteTree(struct Node* root)
{
if (root == NULL) {
return NULL;
}
deleteTree(root-&gt;left);
deleteTree(root-&gt;right);
free(root);
return NULL;
}
void inorder(struct Node*
root) {
if (root != NULL) {
inorder(root-&gt;left);
printf(&quot;%d &quot;, root-&gt;data);
inorder(root-&gt;right);
}}
void preorder(struct Node*
root) {
if (root != NULL) {
printf(&quot;%d &quot;, root-&gt;data);
preorder(root-&gt;left);
preorder(root-&gt;right);
}}
void postorder(struct Node*
root) {
if (root != NULL) {
postorder(root-&gt;left);
postorder(root-&gt;right);
printf(&quot;%d &quot;, root-&gt;data);
}} int main() {
struct Node* root = NULL;
int choice, data;
do {
printf(&quot;\nBinary Tree
Operations:\n&quot;);
printf(&quot;1. Insert\n&quot;);
printf(&quot;2. Delete Tree\n&quot;);
printf(&quot;3. Inorder
Traversal\n&quot;);
printf(&quot;4. Preorder
Traversal\n&quot;);
printf(&quot;5. Postorder
Traversal\n&quot;);
printf(&quot;6. Exit\n&quot;);
printf(&quot;Enter your choice: &quot;);
scanf(&quot;%d&quot;, &amp;choice);
switch (choice) {
case 1:

printf(&quot;Enter data to insert:
&quot;);
scanf(&quot;%d&quot;, &amp;data);
root = insert(root, data);
break;
case 2:
root = deleteTree(root);
printf(&quot;Binary tree
deleted.\n&quot;);
break;
case 3:
printf(&quot;Inorder Traversal: &quot;);
inorder(root);
printf(&quot;\n&quot;);
break;
case 4:
printf(&quot;Preorder Traversal: &quot;);
preorder(root); printf(&quot;\n&quot;);
break;
case 5:
printf(&quot;Postorder Traversal:
&quot;);
postorder(root);
printf(&quot;\n&quot;);
break;
case 6:
printf(&quot;Exiting the
program.\n&quot;);
break;
default:
printf(&quot;Invalid choice. Please
enter a valid
option.\n&quot;);
}}
while (choice != 6);
return 0;
}
