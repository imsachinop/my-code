#include <iostream>
using namespace std;
class node{
    public:
    int data;
    node *next;
    
    node(int value){
        this->data = value;
        this->next = NULL;
    }
};
class stack{
    node *head;
    int size;
    public:
    stack(){
    head = NULL;
    size =0;
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
        node *temp = head;
        while(temp!=NULL){
            cout<<temp->data<<" ";
            temp = temp->next;
        }
        cout<<endl;
    }
    void pop(){
        int x = head->data;
        head = head->next;
        cout<<"popped element is "<< x<<endl;
        size--;
    }
    void top(){
        cout<<head->data;
    }
    void getsize(){
        cout<<"the size of the curretn stack is :"<<size<<endl;
    }
    bool isempty(){
        if(head==NULL){
            cout<<"stack is empty"<<endl;
            return true;
        }
        else{
            cout<<"stack has elememts and it is not empty"<<endl;
            return false;
        }
    }
};

int main(){
    stack s1;
    s1.push(10);
    s1.push(20);
    s1.push(30);
    s1.display();
    s1.pop();
    s1.display();
    cout<<"top elements of the stack is "<<endl;
    s1.top();
    cout<<endl;
    s1.getsize();
    cout<<endl;
    s1.isempty();
}
