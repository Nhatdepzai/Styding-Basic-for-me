# Lý Thuyết:
## I. Quere và stack:
### 1. Quere:
-   Queue:
    -   là một loại cấu trúc dữ liệu và là một loại container adaptor ( theo t hiểu là là 1 loại cấu trúc để chứa dữ liệu có tính sắp xếp ). Hoạt đông theo kiểu **FIFO (First in first out)** có nghĩa là phần tử vào trước sẽ ra trước ( thêm phần tử ở đuôi và lấy phần tử ở đầu).
- Các hoạt động trên Quere:
    -   *enqueue* : thêm 1 phần tử vào đầu hàng đợi. (***Push***)
    -   *dequere* : lấy 1 phần tử ở cuối hàng đợi. (***Pop***)
    -   Top:   xóa 1 phần tử ở cuối hàng đợi.
- Một số phương thức :
    -   *IsFull()* : kiểm tra quere đã đầy chưa.
    -   *IsEmpty()* : kiểm tra hàng đợi còn trống hay không.
- Ứng dụng của Quere:
    - Khử đệ quy.
    - tổ chức lưu vết các quá trình và tìm kiếm theo chiều rộng và quay lui
    - Vét cạn.
    - tổ chức quản lý và phân phối tiến trình trong các hệ điều hành, tổ chức bộ đệm bàn phím.
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
    - vd: đúng vs tên gọi Stack (ngăn xếp) thì các phần tử ra và vào từ cùng 1 hướng.
- Các hoạt động trên Stack:
    -   Push: đẩy 1 phần thử vào đầu ngăn xếp.
    -   pop: xóa 1 phần tử đầu khỏi ngăn xếp.
    -   peek: lấy 1 phần tử đầu của ngăn xếp mà không xóa phần tử đó.
    -   isFull: kiểm tra ngăn xếp đã đầy chưa.
    -   isEmpty: kiểm tra ngăn xếp có rỗng không.
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
    -   là một thuật toán duyệt hoặc tìm kiếm trên một cây hoặc một đồ thị. Thuật toán khởi đầu tại gốc (hoặc chọn một đỉnh nào đó coi như gốc) và phát triển xa nhất có thể theo mỗi nhánh.Thông thường, DFS là một dạng tìm kiếm thông tin không đầy đủ mà quá trình tìm kiếm được phát triển tới đỉnh con đầu tiên của nút đang tìm kiếm cho tới khi gặp được đỉnh cần tìm hoặc tới một nút không có con. Khi đó giải thuật quay lui về đỉnh vừa mới tìm kiếm ở bước trước. Trong dạng không đệ quy, tất cả các đỉnh chờ được phát triển được bổ sung vào một ngăn xếp LIFO.
    Độ phức tạp không gian của DFS thấp hơn của BFS (tìm kiếm theo chiều rộng). Độ phức tạp thời gian của hai thuật toán là tương đương nhau và bằng O(|V| + |E|).
-   Nguyên lý:
    - Khởi đầu từ một đỉnh, đi theo các cung(cạnh) xa nhất có thể. Trở lại đỉnh của cạnh xa nhất, tiếp tục duyệt như trước, cho đến đỉnh cuối cùng.
-   Ứng dụng:
    - Xác định các thành phần liên thông của đồ thị
    - Sắp xếp tô-pô cho đồ thị
    - Xác định các thành phần liên thông mạnh của đồ thị có hướng
    - Kiểm tra một đồ thị có phải là đồ thị phẳng hay không
## 2.Duyệt rộng:
-   Khái niệm:
    - Trong lý thuyết đồ thị, tìm kiếm theo chiều rộng (BFS) là một thuật toán tìm kiếm trong đồ thị trong đó việc tìm kiếm chỉ bao gồm 2 thao tác: (a) cho trước một đỉnh của đồ thị; (b) thêm các đỉnh kề với đỉnh vừa cho vào danh sách có thể hướng tới tiếp theo. Có thể sử dụng thuật toán tìm kiếm theo chiều rộng cho hai mục đích: tìm kiếm đường đi từ một đỉnh gốc cho trước tới một đỉnh đích, và tìm kiếm đường đi từ đỉnh gốc tới tất cả các đỉnh khác. Trong đồ thị không có trọng số, thuật toán tìm kiếm theo chiều rộng luôn tìm ra đường đi ngắn nhất có thể. Thuật toán BFS bắt đầu từ đỉnh gốc và lần lượt nhìn các đỉnh kề với đỉnh gốc. Sau đó, với mỗi đỉnh trong số đó, thuật toán lại lần lượt nhìn trước các đỉnh kề với nó mà chưa được quan sát trước đó và lặp lại. Xem thêm thuật toán tìm kiếm theo chiều sâu, trong đó cũng sử dụng 2 thao tác trên nhưng có trình tự quan sát các đỉnh khác với thuật toán tìm kiếm theo chiều rộng.
-   Đặc điểm:
    - Thuật toán sử dụng một cấu trúc dữ liệu hàng đợi để lưu trữ thông tin trung gian thu được trong quá trình tìm kiếm:
    - Chèn đỉnh gốc vào hàng đợi (đang hướng tới)
    - Lấy ra đỉnh đầu tiên trong hàng đợi và quan sát nó
    - Nếu đỉnh này chính là đỉnh đích, dừng quá trình tìm kiếm và trả về kết quả.
    - Nếu không phải thì chèn tất cả các đỉnh kề với đỉnh vừa thăm nhưng chưa được quan sát trước đó vào hàng đợi.
    - Nếu hàng đợi là rỗng, thì tất cả các đỉnh có thể đến được đều đã được quan sát – dừng việc tìm kiếm và trả về "không thấy".
    - Nếu hàng đợi không rỗng thì quay về bước 2.
-   Ứng dụng:
    - Tìm tất cả các đỉnh trong một thành phần liên thông
    - Thuật toán Cheney cho việc dọn rác
    - Tìm đường đi ngắn nhất giữa hai đỉnh u và v (với chiều dài đường đi tính bằng số cung)
    - Kiểm tra xem một đồ thị có là đồ thị hai phía
    - Thuật toán Cuthill–McKee
    - Thuật toán Ford–Fulkerson để tìm luồng cực đại trong mạng