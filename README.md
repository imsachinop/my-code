#include <iostream>
using namespace std;
template <typename T>
class node{
    public:
    T data;
    node<T> *next;
    
    node(T data){
        this->data = data;
        this->next = NULL;
    }
};
template <typename T>
class stack{
    node<T> *head;
    int size;
    public:
    stack(){
        size=0;
        head =NULL;
    }
    int getsize(){
        return size;
    }
    bool isempty(){
        return size==0;
    }
    void push(T value){
        node<T> *newnode = new node<T>(value);
        if(head==NULL){
            head =newnode;
        }
        else{
            newnode->next = head;
            head = newnode;
        }
        size++;
    }
    T pop(){
        if(size==0){
            return 0 ;
        }
        T val=head->data;
        head = head->next;
        size--;
        return val;
    }
    T top(){
        if(size==0){
            return 0;
        }
        else{
        return head->data;
        }
    }
    void display(){
        node<T> *temp = head;
        while(temp!=NULL){
            cout<<temp->data<<" ";
            temp = temp->next;
        }
        cout<<endl;
    }
    
};
int main(){
    stack<int> s1;
    s1.push(20);
    s1.push(40);
    s1.push(30);
    s1.push(50);
    s1.display();
    s1.pop();
    s1.display();
    cout<<"current size of the stack is: "<<s1.getsize()<<endl;
    cout<<"is stack is empty now: "<<s1.isempty()<<endl;
    cout<<"top elements of the stack is : "<<s1.top()<<endl;

}
