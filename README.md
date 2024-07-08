#include <iostream>
using namespace std;
template <typename T>
class QueueUsingArray{
    T *data;
    int frontindex;
    int nextindex;
    int size;
    int capacity;
    
    public:
    QueueUsingArray(int s){
        data = new T[s];
        frontindex = -1;
        nextindex = 0;
        size = 0;
        capacity = s;
    }
    int getsize(){
        return size;
    }
    bool isempty(){
        return size==0;
    }
    void enqueue(T elements){
        if(size==capacity){
            cout<<"queue is full";
            return;
        }
        data[nextindex]=elements;
        nextindex = (nextindex + 1)%capacity;
        size++;
        if(frontindex==-1){
            frontindex = 0;
        }
    }
    T dequeue(){
        if(size == 0){
            cout<<"queue is empty";
            return 0;
        }
        T temp = data[frontindex];
        frontindex = (frontindex+1)%capacity;
        size--;
        if(size==0){
            frontindex = -1;
            nextindex = 0;
        }
        return temp;
    }
    void display(){
        if(isempty()){
            cout<<"queue is empty you lol"<<endl;
        }
        int i = frontindex;
        for(int count=0;count<size;count++){
            cout<<data[frontindex]<<" ";
            frontindex = (frontindex+1)%capacity;
        }
        cout<<endl;
    }
};
int main(){
    QueueUsingArray<int> s1(5);
    s1.enqueue(10);
    s1.enqueue(20);
    s1.enqueue(30);
    s1.enqueue(40);
    s1.enqueue(50);
    s1.display();
    s1.dequeue();
    s1.dequeue();
    s1.dequeue();
    s1.display();
    cout<<s1.getsize();
}
