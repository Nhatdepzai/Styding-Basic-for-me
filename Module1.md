# So sánh LinkedList và ArrayList

1. Array được cấp phát tĩnh còn LinkedList được cấp phát động.
2. Thao tác trong Array vd như xóa thêm 1 phần tử sẽ tốn rất nhiều chi phí (tốn O(n)) thay vì dùng LinkedList thì chỉ tốn O(1).
3. Tuy nhiên việc truy vấn hay lưu trữ đến 1 phần tử trong Array lại chỉ tốn chi phí là O(1) thay vì tốn O(n) của LinkedList.
4. ### Cái này quan trọng vl này: 
## Bài 1:
~~~
#include <iostream>
using namespace std;
struct node{
    int data;
    node*next;
};
struct List{
    node*head;
    node*tail;
};
void init(List&l){
    l.head=l.tail=NULL;
}
node*getnode(int a){
    node*p=new node;
    p->data=a;
    p->next=NULL;
}
void add_head(List&l, node*p){
    if(l.head==NULL){
        l.head=l.tail=p;
    }
    else{
        p->next=l.head;
        l.head=p;
    }
}
void input(List&l, int a){
    int n;
    for(int i=0;i<a;i++){
        cout<<"nhap gia tri phan tu thu "<<i+1<<endl;
        cin>>n;
        add_head(l,getnode(n));
    }
}
void output(List&l)
{
    for(node*p=l.head;p!=NULL;p=p->next){
        cout<<p->data<<" ";
    }
}
void Add_in_Ist(List &l){
    cout<<"chon vi tri can them"<<endl;
    int stt=0;
    cin>>stt;
    cout<<"chon gia tri can nhap"<<endl;
    int value;
    cin>>value;
    int i=2;
    bool check = false;
    for(node*p=l.head;p!=NULL;p=p->next){
        if(stt==1){
            add_head(l,getnode(value));
            check =true;
            break;
        }
        if(i==stt){
            node*m = getnode(value);
            m->next=p->next;
            p->next=m;
            check = true;
        }
        i++;
    }
    output(l);
    if(check==false){
        cout<<" list del co vi tri nay thua ban :))) "<<endl;
    }
}
void Remove_pt(List &l){
    cout<<"chon vi tri ban muon xoa"<<endl;
    int stt;
    cin>>stt;
    node*c1=l.head;
    int i=2;
    bool check = false;
    for(c1;c1!=NULL;c1=c1->next){
        if(stt==1){
            node*c2=l.head->next;
            l.head=c2;
            check = true;
        }
        else if(i==stt){
           c1->next=c1->next->next;
           check = true;
        }
        i++;
    }
    if(check == false ){
        cout<<" ban bi ranh hang ak :)))) "<<endl;
    }
    output(l);
}
int main(){
    List l;
    init(l);
    int a;
    cout<<"nhap so pt"<<endl;
    cin>>a;
    input(l,a);
    output(l);
    Remove_pt(l);
    return 0;
}

~~~
