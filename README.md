```
#include<iostream>
using namespace std;
class Node{//data types
public:
    int val;
    Node *next;
    Node(int val){
        this->val = val;
        this->next = NULL;
    }
    
};


class Linkedlist{//user defined data structures
public:
    Node *head;
    Node *tail;
    int size;
    Linkedlist(){
        head = tail = NULL;
        size = 0;
    }
    void insertatend(int val){
        Node *temp = new Node(val);
        if(size == 0){
            head = tail = temp;
        }
        else{
            tail->next = temp;
            tail = temp;
        }
        size++;

    }
    void display(){
        Node* temp = head;
        while(temp != NULL){
            cout<<temp->val<<" ";
            temp = temp->next;
        }
        cout<<endl;
    }
    void insertatbegining(int val){
        Node *temp = new Node(val);
        if(size == 0){
            head = tail = temp;
        }
        else{
            temp->next = head;
            head = temp;
        }
        size++;
    }
    void insert(int val, int idx){
        if(idx < 0 || idx > size){
            cout<<"Invalid Index"<<endl;
            return;
        }
        else if(idx == 0){
            insertatbegining(val);
            return;
        }
        else if(idx == size){
            insertatend(val);
            return;
        }
        else{
            Node *t = new Node(val);
            Node*temp = head;
            for (int i = 0; i < idx-1; i++)
            {
                temp = temp->next;
            }
            t->next = temp->next;//connection of idx 3 to temp
            temp->next = t;
            size++;
        }
    }
    void getatidx(int idx){
        Node*temp = head;
        int size = 0;
        while (idx)
        {
            if(size == idx){
                cout<<temp->val;
                break;
            }
            temp = temp->next;
            size++;
        }
        
    }
};
int main(){
    Linkedlist *ll = new Linkedlist();
    ll->insertatend(10);
    ll->display();
    ll->insertatend(20);
    ll->insertatbegining(30);
    ll->insertatbegining(40);
    ll->display();
    ll->insert(80,2);
    cout<<ll->size<<endl;
    ll->display();
    ll->getatidx(2);
    

}

```




