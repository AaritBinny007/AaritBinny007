#include <stdio.h>
#include <string.h>
void ipfix();
int eval();
int pre(char c);
char A[50];
char B[50];
char C[50];
int top = -1;
void main()
{
    int choice;
    do
    {
        printf("\nEnter 1 to Convert Infix to Postfix\n");
        printf("Enter 2 to Evaluate Postfix Expression\n");
        printf("Enter 3 to Exit\n");
        printf("\nEnter your choice: ");
        scanf("%d",&choice);
        switch (choice)
        {
            case 1:
                while (getchar() != '\n');
                printf("Enter Infix Expression: ");
                scanf("%s",A);
                ipfix();
                break;
            case 2:
                while (getchar() != '\n');
                printf("Enter Postfix Expression: ");
                scanf("%s",A);
                int r = eval();
                printf("\nResult = %d\n", r);
                break;
                case 3:
            printf("Exiting...\n");
                break;
                default:
                printf("Invalid choice!!!\n");
        }
}
while (choice!=3);
}
int pre(char c)
{
switch (c)
{
        case '+':
        case '-':
            return 1;
        case '*':
        case '/':
            return 2;
    }
    return -1;
}
void ipfix()
{
int i = 0, j = 0;
    char x;
    while (A[i] != '\0')
    {
        if (A[i] >= '0' && A[i] <= '9')
            B[j++] = A[i];
        else if (A[i] == '(')
            C[++top] = A[i];
        else if (A[i] == ')')
        {
            while (C[top] != '(')
            B[j++] = C[top--];
            top--;
        }
        else
        {
            x = A[i];
            while (top != -1 && C[top] != '(' && pre(C[top]) >= pre(x))
                B[j++] = C[top--];
            C[++top] = x;
        }
        i++;
    }
    while (top != -1)
        B[j++] = C[top--];
    B[j] = '\0';
    printf("Postfix Expression is %s\n", B);
}
int eval()
{
    int stack[20];
    int top = -1;
    int i;
    for (i = 0; A[i] != '\0'; i++)
    {
        if (A[i] >= '0' && A[i] <= '9')
            stack[++top] = A[i] - '0';
        else
        {
            int op2 = stack[top--];
            int op1 = stack[top--];
            switch (A[i])
            {
                case '+':
                    stack[++top] = op1 + op2;
                    break;
                case '-':
                    stack[++top] = op1 - op2;
                    break;
                case '*':
                    stack[++top] = op1 * op2;
                    break;
                case '/':
                    stack[++top] = op1 / op2;
                    break;
            }
        }
    }
    return stack[0];
}
