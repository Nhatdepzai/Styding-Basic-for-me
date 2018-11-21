# Lý Thuyết:
## I. Quere và stack:
### 1. Quere:
-   Quere:
    -   là một loại cấu trúc dữ liệu và là một loại container adaptor ( theo t hiểu là là 1 loại cấu trúc để chứa dữ liệu có tính sắp xếp ). Hoạt đông theo kiểu **FIFO (First in first out)** có nghĩa là phần tử vào trước sẽ ra trước ( thêm phần tử ở đuôi và lấy phần tử ở đầu).
    - vd: đường 1 chiều thì thằng nào vào trước sẽ ra trước :v 
- Các hoạt động trên Quere:
    -   *enquere* : thêm 1 phần tử vào hàng đợi. (***Push***)
    -   *dequere* : xóa 1 phần tử của hàng đợi. (***Pop***)
- Một số phương thức :
    -   *IsFull()* : kiểm tra quere đã đầy chưa.
    -   *IsEmpty()* : kiểm tra hàng đợi còn trống hay không.
- Ứng dụng của Quere:

- Code Quere:
~~~
#include <iostream>

using namespace std;
struct node{
    int data;
    node*next;
};
struct quere1{
    node*head;
    node*tail;
};
void initQ(quere1 &l){
    l.head=l.tail=NULL;
}
node* make_node(int a){
    node*m= new node;
    m->data=a;
    m->next=NULL;
    return m;
}
void PushQ(quere1 &l, int a){
    if(l.head==NULL){
        l.head=l.tail= make_node(a);
    }
    else{
        node*x = make_node(a);
        l.tail->next = x;
        l.tail = x;
    }
}
void OutQ(quere1 &l){
    node*i = l.head;
    while(i!=NULL){
        cout<<i->data<<" ";
        i=i->next;
    }
}
void PopQ(quere1 &l){
    if(l.head==NULL)
        cout<<" em cung del biet xoa gi"<<endl;
    else{
        /*node*ck=l.head;
        ck=ck->next;
        if(ck->next->next==NULL){
            node*m=l.tail;
            l.tail=ck;
            l.tail->next=NULL;
            delete(m); // lam cai nay xoa duoc node cuoi chua m?
        }*/
        // sai cai gi ak m
        /*for(node*m=l.head;m!=NULL;m=m->next){
            if(m->next->next==NULL){
                node*ckl=l.tail;
                l.tail=m;
                l.tail->next=NULL;
                delete(ckl);
            }
        }
        */
        node*p=l.head;
        l.head=l.head->next;
        delete p;
    }
}
int main()
{
    quere1 l;
    initQ(l);
    int k;
    cout<<"nhap so pt cua Q"<<endl;
    cin>>k;
    for(int i=0;i<k;i++){
        int z;
        cout<<"nhap gia tri"<<endl;
        cin>>z;
        PushQ(l,z);
    }
    OutQ(l);
    cout<<"\n";
    PopQ(l);
    OutQ(l);
    return 0;
}
~~~

### 2. Stack:
-   Stack:
    -   cũng là một loại cấu trúc dữ liệu tương tự như là quere. Tuy nhiên thì stack lại hoạt động chỉ theo 1 hướng và theo nguyên tắc **FILO :) (Fisrt in last out)** có nghĩa là phần tử thêm vào đầu tiên thì lại lấy ra cuối cùng.
    - vd: cái lone gì chỉ có 1 nắp mở mà chả cần vậy :v
- Các hoạt động trên Stack:
    -  tương tự như quere nhưng nó khác về cách hoạt động
- Ứng dụng của Stack : Stack có rất nhiều ứng dụng trong tin học như :
    - Chuyển đổi các cơ số (nhị phân, thập phân, bát phân,…)
    - Chuyển biểu thức trung tố sang hậu tố, tính toán các biểu thức hậu tố,…

-   Code hiện thực Stack:
~~~
#include <iostream>
using namespace std;
struct node{
    int data;
    node*next;
};
struct stack1{
    node*head;
};
void initS(stack1 &l){
    l.head=NULL;
}
node* make_node(int a){
    node*m= new node;
    m->data=a;
    m->next=NULL;
    return m;
}
void PushS(stack1 &l, int a){
    node*j=make_node(a);
    if(l.head==NULL){
        l.head=j;
    }
    else{
        j->next=l.head;
        l.head=j;
    }
}
void OutS(stack1 &l){
    node*i = l.head;
    while(i!=NULL){
        cout<<i->data<<" ";
        i=i->next;
    }
}
int main(){
    stack1 l;
    initS(l);
    cout<<"nhap so ptu"<<endl;
    int x;
    cin>>x;
    for(int i=0;i<x;i++){
        cout<<"nhap gtri: "<<endl;
        int z;
        cin>>z;
        PushS(l,z);
    }
    OutS(l);
    return 0;
}
~~~
## II. Heap:
### 1. Khái niệm:
-  Heap là một dạng cấu trúc dữ liệu, là trường hợp đặc biệt của ***cây nhị phân cân bằng*** (là cây dạng nhị phân và các nhánh phải cân bằng vs nhau có nghĩa là 2 bên k được chênh nhau quá 1 nhánh) trong đó, giá trị của nút gốc sẽ được so sánh vs con của nó và được sắp xếp theo các cách khác nhau, và thường thì ta có 2 cách để sắp xếp đó là MaxHeap và MinHeap.
- Do Heap được biểu diễn dưới dạng cây nhị phân mà nút k trên cây sẽ có 2 nút con là 2*k và 2*k+1 và có cha là (k div 2) (đối với array).
-  ***MaxHeap*** là loại Heap mà giá trị của node cha phải lớn hơn giá trị của node con.
- ***MinHeap*** là loại Heap mà giá trị của node cha phải bé hơn giá trị cảu node con.
- Ứng dụng của Heap: 
    -   Ứng dụng chủ yếu của Heap là tìm giá trị lớn nhất hoặc nhỏ nhất trong một tập hợp động.
    -   HeapSort: Dùng để sắp xếp.
    -   Thuật toán đồ thị: Dùng cho đồ thị sử dụng cấu trúc dữ liệu động, chẳng hạn như thuật toán Dijktra hay thuật toán Prim.
- Các hoạt động trên Heap:
    -   BuildHeap: Xây dựng 1 heap (Insert).
    -   Up_heap:   Nếu 1 phần tử lớn hơn cha nó thì đưa đảo vs cha. (MaxHeap).
    -   DownHeap: Nếu 1 phần tử con bé hơn cha nó thì đưa lên đảo vs cha. (MinHeap).
-   Code hiện thực Heap:
~~~

~~~
# III. Duyệt sâu và duyệt rộng:
## 1. Duyệt sâu:
-   Khái niệm:
    -   