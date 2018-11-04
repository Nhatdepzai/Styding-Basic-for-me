# So sánh LinkedList và ArrayList

1. Array được cấp phát tĩnh còn LinkedList được cấp phát động.
2. Thao tác trong Array vd như xóa thêm 1 phần tử sẽ tốn rất nhiều chi phí (tốn O(n)) thay vì dùng LinkedList thì chỉ tốn O(1).
3. Tuy nhiên việc truy vấn hay lưu trữ đến 1 phần tử trong Array lại chỉ tốn chi phí là O(1) thay vì tốn O(n) của LinkedList.

## Bài 1:

#include <iostream>
~~~
using namespace std;
struct node{
    int data;
    node*next;
};
struct List{
    node*head;
    node*tail;
};
void init(List &l){
    l.head=l.tail=NULL;
}
node*getnode(int a){
    node*p=new node;
    p->data=a;
    p->next=NULL;
}
void add_head(List &l, node*p){
    if(l.head==NULL){
        l.tail=l.head=p;
    }
    else{
        p->next=l.head;
        l.head=p;
    }
}
void input(List &l, int a){
    int n;
    for(int i=0;i<a;i++){
        cin>>n;
        add_head(l,getnode(n));
    }
}
void output(List &l)
{
	for(node *p = l.head; p != NULL; p = p ->next)
	{
		cout<<p->data<<" ";
	}
}
int main(){
    List l;
    init(l);
    int a;
    cout<<"nhap so pt"<<endl;
    cin>>a;
    input(l,a);
    output(l);
    return 0;
}
~~~
