/*This file contains 5 functions
********************************************
Preorder
Inoder
Postorder
Double
traversal
********************************************
*/


#include <stdio.h>
#include<stdlib.h>

//Create node
typedef struct node
    {

        int data;
        struct node *left;
        struct node *right;

    }Node;//Making Node as global


//Creating node for tree //
struct node *CreateTree()
{
    
    
    int Nodedata;
    Node *newnode=(Node*)malloc(sizeof(Node)); //dynamically allocate memory to Node

    printf("Enter the data for the nodes(0 for no data)");
    scanf("%d", &Nodedata);

    if(Nodedata==0)
    {
        return NULL; 
    }

      newnode->data=Nodedata;

      printf("Enter the left child data rooted at %d \n",newnode->data);

      newnode->left=CreateTree();

      printf("Enter the right child data rooted at %d\n",newnode->data);

      newnode->right=CreateTree();

      return newnode;
}

void traverse(Node *t)
{

    if(t!=NULL)
    {

        printf("Left child data is %d ",t->data);
        traverse(t->left);
        t=t->right;
    
    }

   if(t!=NULL)
    {
       printf("Right child data is %d\n",t->data);
       traverse(t->right);
    }

}

void Inorder(Node *t)
{
    if(t)
    {
        Inorder(t->left);

        printf("%d ",t->data);

        Inorder(t->right);
    }
}

void Preorder(Node *t)
{
    if(t)
    {
        printf("%d ",t->data);

        Preorder(t->left);

        Preorder(t->right);
    }
}


void Postorder(Node *t)
{
    if(t)
    {
        Postorder(t->left);

        Postorder(t->right);

        printf("%d ",t->data);

    }
}

void Double(Node *t)
{

    if(t)
    {
        printf("%d ",t->data);
        Double(t->left);
        printf("%d ",t->data);
        Double(t->right);
    }
}



int main()
{
    Node *root=CreateTree(); //final return root from function CreateTree
    Node *t=root;   //assign root node to another node t

    printf("\nRoot of the Binary Tree is %d\n ",t->data);

    printf("\n\nPreoder traversing is\n");
    Preorder(t);

    printf("\n\nInorder traversing is\n");
    Inorder(t);
    
    printf("\n\nPostorder traversing is\n");
    Postorder(t);
    
    printf("\n\nDoubleorder traversing is\n");
    Double(t);

    return 1;

}
