#include <iostream>
using namespace std;
class node{
    public:
    int data;
    node *next;
    node(int data)
    {
        this->data = data;
        this->next = NULL;
    }
};
class stack{
    node *head;
    int size;
    public:
    stack(){
    head = NULL;
    size = 0;
    }
    void push(int value){
        node *newnode = new node(value);
        if(head==NULL){
            head = newnode;
        }
        else{
        newnode->next = head;
        head = newnode;
        }
        size++;
    }
    void display(){
    node *temp=head;
    while(temp!=NULL){
        cout<<temp->data<<" ";
        temp = temp->next;
    }
}
};


int main(){
    stack s1;
    s1.push(10);
    s1.push(20);
    s1.display();
}
