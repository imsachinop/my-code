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
class queue{
    node<T> *head;
    node<T> *tail;
    int size;
    public:
    queue(){
        head = NULL;
        tail = NULL;
        size = 0;
    }
    int getsize(){
        return size;
    }
    bool isempty(){
        return size==0;
    }
    T front(){
        if(isempty()){
            cout<<"queue is empty"<<endl;
            return 0;
        }
        return head->data;
    }
    void enqueue(T element){
        node<T> *newnode= new node<T>(element);
        if(head==NULL){
            head = newnode;
            tail = newnode;
            size++;
            return;
        }
        tail->next = newnode;
        tail = tail->next;
        size++;
        return;
    }
    T dequeue(){
        if(isempty()){
            cout<<"queue is empty";
            return 0;
        }
        T temp = head->data;
        head = head->next;
        size--;
        return temp;
    }
};
int main(){
    queue <int> q1;
    q1.enqueue(10);
    cout<<q1.front()<<endl;
    q1.enqueue(20);
    cout<<q1.front()<<endl;
    q1.enqueue(30);
    q1.dequeue();
    cout<<q1.front()<<endl;
}
