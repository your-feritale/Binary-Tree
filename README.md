# Binary-Tree
Program to make binary tree in which we assign some integer value and display the value in some various way

#include <iostream>
#include <stdlib.h>

using namespace std;

struct Node{
	int data;
	Node *left,*right;
};
struct Node *ptr;

struct Node* create(){
	int k;
	struct Node *newNode;
	
	newNode = (struct Node*)malloc(sizeof(Node));
	newNode->left=NULL;
	newNode->right=NULL;
	
	cout<<"Enter data : ";cin>>k;
	if(k==-1){
		return 0;
	}
	newNode->data=k;
	cout<<"Left Child of "<<k<<"\n";
	newNode->left=create();
	cout<<"Right Child of "<<k<<"\n";
	newNode->right=create();
	
	return newNode;
}

void preOrder(struct Node *root){
	if(root==NULL){
		return;
	}
	cout<<root->data<<" ";
	preOrder(root->left);
	preOrder(root->right);
}

void inOrder(struct Node *root){
	if(root==NULL){
		return;
	}
	inOrder(root->left);
	cout<<root->data<<" ";
	inOrder(root->right);
}

void postOrder(struct Node *root){
	if(root==NULL){
		return;
	}
	postOrder(root->left);
	postOrder(root->right);
	cout<<root->data<<" ";
}

int main(){
	struct Node *root;
	cout<<"Enter -1 if you don't want to make Node\n";
	root = create();
	
	cout<<"\nPreorder Traversal\n";
	preOrder(root);
	
	cout<<"\nInorder Traversal\n";
	inOrder(root);
	
	cout<<"\nPostorder Traversal\n";
	postOrder(root);
	
	return 0;
}
