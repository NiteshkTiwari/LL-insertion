# LL-insertion
using linked list
#include<iostream>
using namespace std;

class Node
{
    public:
    int data;
    Node* next;
    Node(int data)
    {
      this->data=data;
      next=NULL;
    }
};

Node* take_input()
{
    int data;
    cin>>data;
    Node* head=NULL;
    Node* tail=NULL;
    while(data!=-1)
    {
        Node* newNode=new Node(data);
        if(head==NULL)
        {
          head=newNode;
          tail=newNode;
        }
        else{
        tail->next=newNode;
        tail=tail->next;
        }
        cin>>data;
    }
   return head;
}

Node* insert(Node* head,int data,int i)
{
    if(head==NULL)
    {
        return NULL ;
    }
    else if(i<1)
    {
        return head;
    }

    else if(i==1)
    {
      Node* newNode=new Node(data);
      Node* temp=head;
      head=newNode;
      head->next=temp;
      return head;
    }
    else
    {
       head->next =insert(head->next,data,i-1);
        
        return head;
    }
}

void print(Node* head)
{
    Node* temp=head;
    while(temp!=NULL)
    {
        cout<<temp->data<<" ";
        temp=temp->next;
    }
}
int main()
{
    Node* head=take_input();
   
   head=insert(head,99,5);
    print(head);
}
