## Đệ quy:
Đệ quy là gì?

Trả lời: Đệ quy là quá trình lặp đi lặp lại theo cùng 1 cách, trong lập trình thì hiểu là gọi 1 hàm trong chính phần thân của nó. :v

## Bài 1:
Đề bài: Cho 1 mảng gồm N phần tử.

a) Sử dụng phương pháp đệ quy để in ra giá trị của N phần tử đó.

b) Sử dụng phương phá đệ quy để in ra tổng giá trị của N phần tử đó.
~~~
#include <iostream>

using namespace std;
void printArray(int*m, int a){
    static int k=0;
    cout<<m[0]<<" ";
    k++;
    if(k==a){
        return ;
    }else{
        return printArray(m+1,a);
    }
}
void SumArray(int*m, int a){
    static int sum=0,h=0;
    sum+=m[0];
    h++;
    if(h==a){
            cout<<"\n";
        cout<<sum;
        return ;
    }
    else{
        return SumArray(m+1,a);
    }
}
int main()
{
    int m[6]={1,2,3,4,5,6};
    printArray(m,6);
    SumArray(m,6);
    return 0;
}

~~~

## Bài 2:
Đề bài: 
Input: N

a) Liệt kê các dãy nhị phân có độ dài là N, từ nhỏ đến lớn ( 0000...000 ->1111...1111)

b) Liệt kê các hoán vị của Tập hợp các số từ 1 .. N.

Ví dụ cho câu b: Các hoán ví của 3 phần tử là:(1,2,3), (1,3,2) ,(2,1,3),(2,3,1),(3,1,2),(3,2,1)




