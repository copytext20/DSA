#include<bits/stdc++.h>
using namespace std;

class Node{
    public:
    int data;
    Node *next;

    Node(int val){
        data = val;
        next = NULL;
    }
};


// Function to insert at beginning
void insertAtBeginning(Node* &head, int d){
    //new node create 
    Node* newNode = new Node(d);
    newNode->next = head;
    head = newNode;
}


// Function to insert at End
void insertAtEnd(Node* &tail, int d){

    Node* newNode = new Node(d);
    tail->next = newNode;
    tail = newNode;
}


// Function to insert at any position
void insertAtPosition(Node* &head, Node* &tail, int position, int d){

    Node* temp = head;
    
    // insert at first position
    if(position == 1){
        insertAtBeginning(head,d);
        return;
    }

    // insert at last position
    if(temp->next == NULL){
        insertAtEnd(tail,d);
        return;
    }
    
    int i=1;

    while(i<position-1){
        temp = temp->next;
        i++;
    }

    Node* newNode = new Node(d);

    newNode->next = temp->next;
    temp->next = newNode;

}


// Function to delete at Head

void deleteAtHead(Node* &head){

    Node* temp = head;
    head = head->next;
    free(temp);
}


// Function to search data in Node

void nodeSearch(Node* &head, int key){

    Node* temp = head;
    int flag=0;

    while(temp!=NULL){
        if(temp->data == key){
            flag=1;
        }
        temp = temp->next;
    }

    if(flag==1){
        cout<<"Found"<<endl;
    }
    else{
        cout<<"Not Found"<<endl;
    }

}

void print(Node* head){
    Node* temp;
    temp = head;

    while(temp!=NULL){
        cout<<temp->data<<endl;
        temp = temp-> next;
    }     
}


int main()
{
    Node* node1 = new Node(10);

    Node* head = node1;
    Node* tail = node1;

    insertAtBeginning(head,12);
    insertAtEnd(tail,16);
    insertAtPosition(head,tail,2,22);
    deleteAtHead(head);
    nodeSearch(head,16);

    print(head);

    return 0;
}
