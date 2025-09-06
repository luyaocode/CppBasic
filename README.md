# CppBasic
## C++非虚函数的静态绑定
#include <iostream>
using namespace std;
class CBanana
{
public:
        void eat()
        {
                cout<<"This Addr: "<<this<<endl;
                cout<<"You ate 1 banana."<<endl;
        }
};
int main()
{
        CBanana* pBanana=new CBanana;
        pBanana = nullptr;
        pBanana->eat();
        return 0;
}

Output:
This Addr: 0
You ate 1 banana.
由于 eat() 是非虚函数，编译器直接生成调用 CBanana::eat() 函数地址的指令，不需要通过对象查找。
即使 pBanana 是 nullptr，只要函数不访问成员变量（即不使用 this 指针），就不会触发内存错误 —— 因为函数地址在编译时已确定，调用过程不需要访问对象内存。
