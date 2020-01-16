<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Effective C++](#effective-c)
  - [1. 让自己习惯C++](#1-%E8%AE%A9%E8%87%AA%E5%B7%B1%E4%B9%A0%E6%83%AFc)
    - [01. 视C++为一个语言联邦](#01-%E8%A7%86c%E4%B8%BA%E4%B8%80%E4%B8%AA%E8%AF%AD%E8%A8%80%E8%81%94%E9%82%A6)
    - [02. 尽量以 const, enum, inline 替换 #define](#02-%E5%B0%BD%E9%87%8F%E4%BB%A5-const-enum-inline-%E6%9B%BF%E6%8D%A2-define)
    - [03. 尽可能使用 const](#03-%E5%B0%BD%E5%8F%AF%E8%83%BD%E4%BD%BF%E7%94%A8-const)
    - [04. 确定对象被使用前已先被初始化](#04-%E7%A1%AE%E5%AE%9A%E5%AF%B9%E8%B1%A1%E8%A2%AB%E4%BD%BF%E7%94%A8%E5%89%8D%E5%B7%B2%E5%85%88%E8%A2%AB%E5%88%9D%E5%A7%8B%E5%8C%96)
  - [2. 构造/析构/赋值运算](#2-%E6%9E%84%E9%80%A0%E6%9E%90%E6%9E%84%E8%B5%8B%E5%80%BC%E8%BF%90%E7%AE%97)
    - [05. 了解C++默默编写并调用哪些函数](#05-%E4%BA%86%E8%A7%A3c%E9%BB%98%E9%BB%98%E7%BC%96%E5%86%99%E5%B9%B6%E8%B0%83%E7%94%A8%E5%93%AA%E4%BA%9B%E5%87%BD%E6%95%B0)
    - [06. 若不想使用编译器自动生成的函数，就该明确拒绝](#06-%E8%8B%A5%E4%B8%8D%E6%83%B3%E4%BD%BF%E7%94%A8%E7%BC%96%E8%AF%91%E5%99%A8%E8%87%AA%E5%8A%A8%E7%94%9F%E6%88%90%E7%9A%84%E5%87%BD%E6%95%B0%E5%B0%B1%E8%AF%A5%E6%98%8E%E7%A1%AE%E6%8B%92%E7%BB%9D)
    - [07. 为多态基类声明虚析构函数](#07-%E4%B8%BA%E5%A4%9A%E6%80%81%E5%9F%BA%E7%B1%BB%E5%A3%B0%E6%98%8E%E8%99%9A%E6%9E%90%E6%9E%84%E5%87%BD%E6%95%B0)
    - [08. 析构函数不要抛出异常](#08-%E6%9E%90%E6%9E%84%E5%87%BD%E6%95%B0%E4%B8%8D%E8%A6%81%E6%8A%9B%E5%87%BA%E5%BC%82%E5%B8%B8)
    - [09. 绝不在构造和析构过程中调用虚函数](#09-%E7%BB%9D%E4%B8%8D%E5%9C%A8%E6%9E%84%E9%80%A0%E5%92%8C%E6%9E%90%E6%9E%84%E8%BF%87%E7%A8%8B%E4%B8%AD%E8%B0%83%E7%94%A8%E8%99%9A%E5%87%BD%E6%95%B0)
    - [10. 令一个 operator= 返回一个 reference to *this](#10-%E4%BB%A4%E4%B8%80%E4%B8%AA-operator-%E8%BF%94%E5%9B%9E%E4%B8%80%E4%B8%AA-reference-to-this)
    - [11. 在 operator= 中处理 “自我赋值”](#11-%E5%9C%A8-operator-%E4%B8%AD%E5%A4%84%E7%90%86-%E8%87%AA%E6%88%91%E8%B5%8B%E5%80%BC)
    - [12. 复制对象时勿忘其每一个成分](#12-%E5%A4%8D%E5%88%B6%E5%AF%B9%E8%B1%A1%E6%97%B6%E5%8B%BF%E5%BF%98%E5%85%B6%E6%AF%8F%E4%B8%80%E4%B8%AA%E6%88%90%E5%88%86)
  - [3. 资源管理](#3-%E8%B5%84%E6%BA%90%E7%AE%A1%E7%90%86)
    - [13. 以对象管理资源](#13-%E4%BB%A5%E5%AF%B9%E8%B1%A1%E7%AE%A1%E7%90%86%E8%B5%84%E6%BA%90)
    - [14. 在资源管理类中小心 copying 行为](#14-%E5%9C%A8%E8%B5%84%E6%BA%90%E7%AE%A1%E7%90%86%E7%B1%BB%E4%B8%AD%E5%B0%8F%E5%BF%83-copying-%E8%A1%8C%E4%B8%BA)
    - [15. 在资源管理类中提供对原始资源的访问](#15-%E5%9C%A8%E8%B5%84%E6%BA%90%E7%AE%A1%E7%90%86%E7%B1%BB%E4%B8%AD%E6%8F%90%E4%BE%9B%E5%AF%B9%E5%8E%9F%E5%A7%8B%E8%B5%84%E6%BA%90%E7%9A%84%E8%AE%BF%E9%97%AE)
    - [16. 成对使用 new 和 delete 时要采取相同形式](#16-%E6%88%90%E5%AF%B9%E4%BD%BF%E7%94%A8-new-%E5%92%8C-delete-%E6%97%B6%E8%A6%81%E9%87%87%E5%8F%96%E7%9B%B8%E5%90%8C%E5%BD%A2%E5%BC%8F)
    - [17. 以独立语句将 newed 对象置入智能指针](#17-%E4%BB%A5%E7%8B%AC%E7%AB%8B%E8%AF%AD%E5%8F%A5%E5%B0%86-newed-%E5%AF%B9%E8%B1%A1%E7%BD%AE%E5%85%A5%E6%99%BA%E8%83%BD%E6%8C%87%E9%92%88)
  - [4. 设计与声明](#4-%E8%AE%BE%E8%AE%A1%E4%B8%8E%E5%A3%B0%E6%98%8E)
    - [18. 让接口容易被正确使用，不易被误用](#18-%E8%AE%A9%E6%8E%A5%E5%8F%A3%E5%AE%B9%E6%98%93%E8%A2%AB%E6%AD%A3%E7%A1%AE%E4%BD%BF%E7%94%A8%E4%B8%8D%E6%98%93%E8%A2%AB%E8%AF%AF%E7%94%A8)
    - [19. \*\* 设计 class 犹如设计 type (这条十分重要) \*\*](#19-%5C%5C-%E8%AE%BE%E8%AE%A1-class-%E7%8A%B9%E5%A6%82%E8%AE%BE%E8%AE%A1-type-%E8%BF%99%E6%9D%A1%E5%8D%81%E5%88%86%E9%87%8D%E8%A6%81-%5C%5C)
    - [20. 宁以 pass-by-reference-to-const 替换 pass-by-value](#20-%E5%AE%81%E4%BB%A5-pass-by-reference-to-const-%E6%9B%BF%E6%8D%A2-pass-by-value)
    - [21. 必须返回对象时，别妄想返回其引用](#21-%E5%BF%85%E9%A1%BB%E8%BF%94%E5%9B%9E%E5%AF%B9%E8%B1%A1%E6%97%B6%E5%88%AB%E5%A6%84%E6%83%B3%E8%BF%94%E5%9B%9E%E5%85%B6%E5%BC%95%E7%94%A8)
    - [22. 将成员变量声明为 private](#22-%E5%B0%86%E6%88%90%E5%91%98%E5%8F%98%E9%87%8F%E5%A3%B0%E6%98%8E%E4%B8%BA-private)
    - [23. 宁以 non-member、non-friend、替换 member 函数](#23-%E5%AE%81%E4%BB%A5-non-membernon-friend%E6%9B%BF%E6%8D%A2-member-%E5%87%BD%E6%95%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


# Effective C++

## 1. 让自己习惯C++
### 01. 视C++为一个语言联邦
1. C++不仅仅是C加上面向对象特性。而且还有模板、异常、重载、STL等等。。。
2. C++并不是一个带有一组守则的一体语言，它是由四个次语言自称的联邦政府
    - C
    - Object-Oriented C++
    - Template C++
    - STL
---
### 02. 尽量以 const, enum, inline 替换 #define

     "宁可以编译器替换预处理器"
1. __使用 const 代替 #define__  
    ```cpp
    #define ASPECT_RATIO 1.653
    ```
    这个记号 ASPECT_RATIO 可能并未进入记号表，从而可能会得到编译错误。而且预处理器盲目地将"ASPECT_RATIO"替换为 1.653， 这可能会导致目标码(object code)出现多份 1.653
    
    所以可使用常量替换上边的宏：
    ```cpp
    const double AspectRatio = 1.653;
    ```

2. __使用 enum 代替 #define__
    ```cpp
    class GamePlayer{
    private:
        enum {NumTurns = 5};
        int scores[NumTurns];
    };
    ```
    enum 的行为比较像 #define 而不像 const，例如取一个 const 的地址是合法的，而取 enum 的地址不合法。enum 和 #define 一样不会导致非必要的内存分配。

3. __使用模板内联函数代替宏定义函数__
    ```cpp
    #define CALL_WITH_MAX(a, b) f((a) > (b) ? (a) : (b))
    ```
    就非常丑，而且在某些特殊情况下会有很麻烦的问题。
    ```cpp
    template<typename T>
    inline void callWithMax(const T& a, const T& b){
        f(a > b ? a : b);
    }
    ```
    这样的模板内联函数会更好，而且它遵守作用域和访问规则，因为是一个真正的函数。
---
### 03. 尽可能使用 const
1. __const 和一般对象与指针一起使用__  
 const 和指针一起使用有四种情况。只需要记住：__如果 const 出现在星号左边，表示被指对象是常量；const 出现在星号右边，表示指针自身是常量；同时出现在左右两边则都是常量。__
    ```cpp      
    char greeting[] = "Hello";
    char* p = greeting;         // 都不是常量
    const char* p = greeting;   // 被指对象是常量
    char* const p = greeting;   // 指针是常量
    const char* const p = greeting; // 都是常量
    ```

2. __const 和STL迭代器一起使用__  
    对于STL迭代器，如果声明迭代器为 const，就像声明指针为 const 一样，表明这个迭代器不得指向其他对象；而如果希望指明迭代器所指的对象不可改动，需要使用 const_iterator.

3. __const 和函数一起使用__  
    - 在一个函数声明式内，const 可以和函数返回值、各个参数、函数自身(如果函数是成员函数)产生关联。
        - 将函数返回值声明为 const，可以使其不会再被赋值。
        - const 参数，在不打算修改传入的值时要把形参声明为 const。
        - const 成员函数，该函数不可以修改自身对象的任何 non-static 成员变量。

4. 使用 const 的目的在于让编译器帮助测试出错误用法。

---
### 04. 确定对象被使用前已先被初始化

1. 读取未初始化的值会导致不明确的行为。对内置类型，需要手动完成初始化；对于内置类型以外的对象，由构造函数完成初始化。

2. 用构造函数对成员进行初始化时，要使用成员初始化器而不是在构造函数体中进行初始化。这样可以避免二次初始化，而且效率更高。为了不用去特意记住哪些变量已被初始化哪些未被初始化，可以规定总是在初始化器中初始化所有的成员变量。

3. 对于不同编译单元内的 __非局部静态变量(全局变量)__，它们的初始化顺序是不确定的，因此是很危险的。 所以，可以将每个非局部静态变量搬到自己的专属函数内进行初始化(在函数内声明为static)，这些函数返回一个指向该局部静态变量的引用。然后调用这样的函数，而不是直接去访问对象本身(因为直接访问对象本身，该对象可能还未被初始化)。这也是 __单例模式__ 的一个常见实现手法。 但是这种函数"内含 static 对象"的情况在多线程系统中是违反线程安全的，解决办法是可以在程序单线程启动阶段手动调用一遍所有这种返回局部静态变量引用的函数。


---
## 2. 构造/析构/赋值运算

### 05. 了解C++默默编写并调用哪些函数

1. 当写下：
    ```cpp
    class Empty { };
    ```
    就好像写下这样的代码：
    ```cpp
    class Empty{
    public:
        Empty() { ... }                            // 默认构造函数
        Empty(const Empty& rhs)                    // 拷贝构造函数
        ~Empty() { ... }                           // 析构函数

        Empty& operator=(const Empty& rhs){ ... }  // 重载的 = 运算符
    };
    ```
    其余部分都是编译器默认实现的，而且是 inline 的，而且只有当它们被调用时才会被编译器创建。 
    
2. 编译器产生的虚构函数是非虚函数，除非这个类的基类将析构函数声明为虚函数。 

3. 对于拷贝构造函数和重载的赋值运算符，编译器只是将源对象的每一个非静态成员变量拷贝到目标对象。

4. 当显示地提供了构造函数后，编译器就不会再创建默认构造函数，因此无需担心编译器的版本覆盖掉自定义的版本。

5. 对内含引用成员的类对象的赋值操作，以及内含 const 成员的类对象的赋值操作，编译器会拒绝生成默认的重载 = 运算符函数，这样的行为需要自己定义。因为更改引用所指向的对象，和更改 const 对象，在C++中都是不合法的。

---
### 06. 若不想使用编译器自动生成的函数，就该明确拒绝

1. 如果不想支持拷贝操作和赋值操作，可以 __将拷贝构造函数和重载赋值运算符函数声明为 private 函数，并且不去实现__。 这样可以避免编译器自动生成默认的函数，而且如果成员函数或友元函数尝试调用这样的函数，连接器会报错(因为只有声明没有定义)。 例如：
    ```cpp
    class HomeForSale{
    public:
        ...
    private:
        HomeForSale(const HomeForSale& );               // 只有函数声明
        HomeForSale& operator=(const HomeForSale& );
    };
    ```

2. 还有一种方法是，声明一个基类，然后将想要实现上述功能的类继承自该基类。 这样的好处一个是重用，再一个是可以把连接器的错误转化成编译时错误。
    ```cpp
    class Uncopyable{
    protected:
        Uncopyable() {}                 // 允许派生类对象对该基类进行构造和析构
        ~Uncopyable() {}
    private:
        Uncopyable(const Uncopyable&);  // 但是不允许复制操作
        Uncopyable& operator=(const Uncopyable&)
    };l
    ```
    ```cpp
    // 我们的类只需要 private 继承 Uncopyable 即可
    class HomeForSale: private Uncopyable{
        ...
    }
    ```
    当任何人，包括成员函数和友元函数尝试调用 HomeForSale 的拷贝构造函数和赋值运算符函数时，编译器生成的 HomeForSale 的对应函数会尝试调用基类的对应函数，而基类中已声明为 private，从而会导致编译错误。
---
### 07. 为多态基类声明虚析构函数

1. 假设 __工厂（factory）函数__，返回一个基类指针，指向一个派生类对象，派生类对象在堆中。为了避免内存泄漏，在用完这个指针后，需要将其 delete。

2. 这样做的问题在于：  
    - 依赖客户来做内存释放，不靠谱（见条款13）
    - 而且，返回的是 __指向派生类对象的基类指针__，而 delete 时，如果基类析构函数不是虚函数，则只会调用基类的析构函数而不是派生类的析构函数。从而产生未定义行为（通常是基类部分对象被析构，而派生类的成员未被释放）。

3. 对于不会作为基类的类，声明虚析构函数会导致其占用空间增加（因为要维护虚函数表和指向虚函数表的指针）。一般 __只有当类内含有至少一个虚函数时，才将其析构函数声明为 virtual__

4. 所有 STL 的容器都不含虚析构函数，所以自定义类继承自这些类时，都有可能会出现上述问题。

---
### 08. 析构函数不要抛出异常

1. __C++ 不鼓励析构函数抛出异常__ 因为当释放一个 vector\<Obj\> 或 array\<Obj\> 时，中间可能会抛出两个或以上的异常，这会导致未定义行为。

2. 解决方法，可以用 RAII 的方法，嵌套一个用于管理资源的类：  
    ```cpp
    class Connection{
    public:
        static Connection create();     // 返回 Connection 对象

        void close();                   // 关闭 Connection，可以抛出异常
    }

    class Conn{                         // 资源管理类
    public:
        void close(){
            con.close();
            closed = true;
        }

        ~Conn(){
            if(!closed){
                try{
                    con.close();
                }catch (...){
                    std::abort();       // 一旦 close 抛出异常则结束程序
                }
            }
            
        }
    private:
        Connection con;
        bool closed;
    }
    ```
    Conn类自己提供了一个 close() 函数，用来给客户一个处理异常的机会。  
    就算客户不想用这个功能，可以直接调用 Conn 类的析构函数或者忽略(等自动析构)，一旦在析构时，close()函数抛出异常，可以选择结束程序（abort） 或 将异常吞掉。

---
### 09. 绝不在构造和析构过程中调用虚函数

1. 因为如果基类的构造函数中调用了虚函数，而派生类对象在构造时，会先调用基类的构造函数（基类构造函数调用早于派生类构造函数），这时基类构造函数调用的虚函数，执行的是基类自身的版本，而不是派生类中 overried 的版本。所以就算它是虚函数，调用的也还是基类版本。换句话说，这时虚函数其实就不是虚函数了。

2. 原因在于，派生类调用基类构造函数时，这个对象相当于是一个基类对象，只能访问基类的成员变量，所以只能调用基类版本的虚函数。

3. 对于析构函数也是一样，因为当执行到基类的析构函数时，派生类的部分已经被销毁了（派生类析构函数调用早于基类析构函数），所以析构函数中的虚函数调用时，调用的仍然是基类的版本。

4. 解决方法在于，可以从派生类将一些信息传递给基类的构造函数，而不是调用虚函数。

---
### 10. 令一个 operator= 返回一个 reference to *this

1. 这样做主要是解决连锁赋值的问题，如
    ```cpp
    int x, y, z;
    x = y = z = 10;
    ```
    重载形式：
    ```cpp
    Widget& operator=(const Widget& rhs){    // 注意这里返回的是引用
        ...  // 一系列赋值操作
        return *this;
    }
    ```
    这里返回左手边的引用，从而可以实现连续赋值。

2. 只是一个协议，让重载后 = 的行为跟内置 = 的行为一致，不算是一个 bug. 当然 +=, -= 也要这样做。


---
### 11. 在 operator= 中处理 “自我赋值”

1. 有时候程序会存在潜在的自我赋值行为。 例如 a[i] = a[j]， *px = *py，等。而潜在的问题在于：
    ```cpp
    Widget& operator=(const Widget& rhs){
        delete ptr;
        ptr = new Obj(*(rhs.ptr));
        return *this.
    }
    ```
    当 rhs 与当前对象是同一个对象时，就会gg。所以需要加以判断：
    ```cpp
    if(this == &rhs)                // 这里的检测是直接对对象地址进行检测
        return *this;       
    ```

2. 更进一步的说，上边的代码仍然不能保证“异常安全性”，因为 new Obj()；调用可能导致异常。这里可以使用所谓的 __copy and swap__ 技术。下面是一个好的 operator= 的实现：
    ```cpp
    void swap(Widget& rhs);         // 交换*this 和 rhs 的数据

    Widget& operator=(const Widget& rhs){
        Widget temp(rhs);           // 拷贝构造函数，将 rhs 数据制作一份副本
        swap(temp);                 // 将副本数据拷贝到自身    
        return *this;
    }
    ```

---
### 12. 复制对象时勿忘其每一个成分

1. 设计良好的类只留两个函数用来拷贝，这里统一称作拷贝函数：
    - 拷贝构造函数
    - 重载的 operator=

2. 第一个问题：__当成员初始化器中漏掉成员变量，编译器也不会报错__。所以当添加了新成员变量时，要记得把它的初始化也加入初始化器中。

3. 第二个问题：__任何时候在写派生类的拷贝函数时，必须很小心地复制其基类的成分__。很多基类成分是 private 的，需要调用基类相应的函数来复制。例如在派生类的初始化器中调用基类的拷贝构造函数，在重载的 operator= 函数中调用基类的 operator=。
    ```cpp
    DerivedClass(const DerivedClass& rhs)
        : BaseClass(rhs),                   // 派生类拷贝构造函数
          ...                               // 初始化派生类成员
    {      

    }

    DerivedClass& operator=(const DerivedClass& rhs){
        BaseClass::operator=(rhs);          // 对基类成分进行赋值
        ...                                 // 对派生类成分赋值

        return *this;                       
    }

    ```

4. 另外，虽然功能相似，但不要让这两个拷贝函数互相调用，因为那样是没有意义的。
    - 如果令 operator= 调用拷贝构造函数，相当于创建一个已经创建了的对象。
    - 如果令拷贝构造函数调用 operator=，自身构造还未完成，未初始化，就进行赋值，也是没有意义的。

    所以如果两个拷贝函数有很多相同代码，可以将这部分代码封装进第三个函数。

---
## 3. 资源管理

资源不仅包括动态分配的内存，还包括很多其他资源类型。重要的是，__不论哪种资源，当不再使用它时，必须将它还给系统__。  


### 13. 以对象管理资源

1. 依然是之前的工厂例子，工厂函数返回一个指针，而且函数的调用者有责任在用完后将其释放，但由于很多因素（例如中途发生异常、提早return、continue等等），会导致最后的 delete 操作无法执行。所以，只是单纯依赖调用者会执行 delete 将工厂产生的指针指向的内存释放掉，是行不通的。

2. 为了确保工厂函数返回的对象总能够被释放，__需要将资源放进对象内，当控制流离开当前域，该对象的析构函数会自动调用从而释放资源__。这就是：以对象管理资源。核心在于依赖C++ 的“析构函数自动调用机制”来确保资源被释放。

3. “以对象管理资源”的两个关键想法：
    - __获得资源后立刻放进管理对象内__。也就是 RAII 的思想。
    - __管理对象(外层嵌套的对象)运用析构函数确保资源被释放__。不论控制流如何离开区块，一旦对象被销毁，其析构函数自然会被自动调用，于是资源被释放。

4. 还有一种方法是使用 __智能指针 shared_ptr__，详见 
[智能指针笔记: 智能指针和异常](https://github.com/AlanChaw/cpp_review/blob/master/C%2B%2B%E6%99%BA%E8%83%BD%E6%8C%87%E9%92%88%E5%92%8C%E5%86%85%E5%AD%98%E7%AE%A1%E7%90%86.md#4-%E6%99%BA%E8%83%BD%E6%8C%87%E9%92%88%E5%92%8C%E5%BC%82%E5%B8%B8)

---
### 14. 在资源管理类中小心 copying 行为

1. 对于条款13，并非所有的资源都在堆中，对那种资源，智能指针可能不适合作为资源掌控者(resource handlers)。因此，需要建立自己的资源管理类。

2. __问题：当一个 RAII 对象被复制，会发生什么事？__ 会有以下两种可能：
    - __禁止复制__。在有些情况下，对 RAII 对象的复制是不合理的 （例如互斥器，构造时加锁，析构时解锁），这时需要禁止复制（用条款6中的方法，将拷贝函数设为 private）。

    - __对底层资源使用引用计数__。其实就相当于 shared_ptr 干的事，当最后一个引用被销毁时，资源自动释放。 但对 RAII 对象的复制操作要保证是 __深复制__，即复制一个 RAII 对象时，必须一并复制其管理的资源。因为如果多个 RAII 对象管理同一份资源，会导致 空悬指针 的问题。

---
### 15. 在资源管理类中提供对原始资源的访问

1. 有时候需要 ”玷污双手“，跳过资源管理类直接访问其中的资源，而 RAII 类需要提供一个方法来使用户可以访问到其中的原始资源。
    - 对于 shared_ptr，可以调用 ptr.get() 函数来获取其中存储的指针，也可以用 -> 操作符直接调用其中存储的指针的成员函数。
    - 对于 RAII 对象，如果提供一个显示的函数返回其中的资源，那这个 RAII 对象就成了脱裤子放屁。因为 RAII 对象存在的目的就是为了防止其中的资源泄漏，提供一个直接访问其中资源的函数就破坏了这种防护。
        ```cpp
        class RAII_Class{
        public:
            Resource get() const{       // 显示转换函数
                return r;
            }

        private:
            Resource r;
        }
        ```
        实际上，也可以提供一种隐式转换函数：
        ```cpp
        class RAII_Class{
        public:
            ...
            operator Resource() const{   // 隐式转换函数
                return r;
            }
            ...
        }

        ```
        然而隐式转换也增加了错误发生的风险，可能发生非故意的类型转换，而且不会报错。

2. 所以，通常显示地进行转换（提供get函数），还是比较好的（更安全）。但是提供隐式转换会更加方便，这个事也比较有争论。但是归根到底要记住，__RAII 管理类不是为了封装某个资源而存在，而是为了确保资源释放一定会发生。__

---
### 16. 成对使用 new 和 delete 时要采取相同形式

1. 在分配内存时使用了 new[]，在释放时也要使用 delete[]。 实际上 new[] 和 new 是不同的操作符。

2. 这个事情说起来容易，但是做起来难。例如：
    ```cpp
    typedef std::string AddressLines[4];    // AddressLines是一个数组

    std::string* pal = new AddressLines;    // 这里实际上是一个 new[]
    ```
    所以，最好尽量不要对数组形式做 typedef。而且应该尽量避免动态分配对象数组，最好用 string 或 vector 等模板类。这些类可以将对数组的需求几乎降为0.

---
### 17. 以独立语句将 newed 对象置入智能指针

1. shared_ptr 和 new 结合使用的具体解释，可以参考 [智能指针笔记：shared_ptr 和 new 结合使用](https://github.com/AlanChaw/Cpp_notes/blob/master/C%2B%2B%E6%99%BA%E8%83%BD%E6%8C%87%E9%92%88%E5%92%8C%E5%86%85%E5%AD%98%E7%AE%A1%E7%90%86.md#3-shared_ptr-%E5%92%8C-new-%E7%BB%93%E5%90%88%E4%BD%BF%E7%94%A8)，要记住的是： __智能指针不支持隐式类型转换__ 即：把一个普通指针直接赋值给智能指针是错误的。

2. 假设有如下例子：
    ```cpp
    // 函数声明
    int priority();
    void processWidget(shared_ptr<Widget> pw);

    // 函数调用
    processWidget(new Widget, priority());          // 错误！

    processWidget(shared_ptr<Widget>(new Widget), priority())   // 正确
    ```

    对于第二种正确调用，虽然这里用了智能指针，但是还是可能泄漏资源。实参 shared_ptr<Widget>(new Widget) 由两部分组成：
    - 执行 "new Widget" 
    - 调用 shared_ptr 构造函数  
    
    于是在调用 processWidget 函数之前，编译器必须做以下三件事：  
    - 调用 priority()
    - 执行 "new Widget"
    - 调用 shared_ptr 构造函数

    但是实际上编译器做事情的顺序可能是：
    - 执行 "new Widget"
    - 调用 priority()
    - 调用 shared_ptr 构造函数

    这就导致一旦 priority() 执行发生异常，new Widget 将会资源泄漏，因为此时智能指针还未被初始化。

3. 而要避免上述问题，只需要以独立语句将 new 置入智能指针：
    ```cpp
    shared_ptr<Widget> sp(new Widget);

    processWidget(sp, priority());          // 这里一定不会发生泄漏
    ```

---
## 4. 设计与声明

### 18. 让接口容易被正确使用，不易被误用

1. 要考虑到客户在使用接口时可能会犯什么样的错误。

2. 除非有好的，否则应该尽量令你的自定义类型的行为与内置类型一致。即：__避免无端与内置类型不兼容。__ 例如，STL提供的接口就很一致，每个容器都有一个 size()函数。不像 Java，一会 length 一会又 size() 的。

3. 任何接口如果要求客户必须记得做某些事情，就是有着“不正确使用”的倾向，例如前边的工厂函数直接返回一个动态分配的对象，这要求客户要记得去释放。 一般好的实现可以使用 RAII 封装，也可以让工厂函数直接返回一个智能指针。

4. shared_ptr 会自动使用它的“每个指针专属的删除器“，这可以防止 cross-DDL-problem，即“对象在动态链接程序库（DDL）中被 new 创建，却在另一个 DDL 内被 delete 销毁”。因为 shared_ptr 默认的删除器是来自 shared_ptr 。

    - 跨DDL释放问题：在一个程序A中调用了另一个动态链接库B提供的接口，而B使用 new 或 malloc 申请了一块内存，并返回句柄给调用者A，A尝试释放该内存会发生错误，一种解决方法是使用B提供的接口释放该内存。

---
### 19. \*\* 设计 class 犹如设计 type (这条十分重要) \*\*

1. 当定义了一个新的类(class)，就定一个了一个新类型(type)。

2. 在设计一个新的类时，请考虑下问题：
    - __新类型的对象应该被如何创建和销毁？__   
        - 构造函数
        - 析构函数
        - 重载的 new, new[], delete, delete[] 运算符

    - __对象的初始化和对象的赋值应该有什么样的差别？__ 
        - 拷贝构造函数
        - 重载的赋值运算符

    - __新类型的对象如果被 pass by value，意味着什么？__ 
        - 拷贝构造函数

    - __什么是新类型的”合法值“？__ 
        - 数值的约束条件（invariants）
        - 构造函数、重载赋值操作符、setter函数要进行错误检查工作。

    - __你的新类型需要配合某个继承图系（inheritance graph）吗？__
        - 如果是派生类，需要考虑基类的 virtual 和 non-virtual 函数
        - 如果允许其他类继承自你的类，需要将特定函数设置为 virtual (尤其是析构函数)

    - __你的新类型需要什么样的转换？__
        - 是否支持隐式类型转换 ?
        - 如不支持，要明确将只有一个参数的构造函数声明为 __explicit__

    - __什么样的操作符和函数对此新类型是而言是合理的？__
        - 决定将哪些函数设置为成员函数，哪些不是

    - __什么样的标准函数应该被驳回？__
        - 条款6，当前类不允许被拷贝，则要把拷贝构造函数和重载赋值运算符声明为 private，以拒绝编译器为我们自动生成。

    - __谁该取用新类型的成员？__
        - 决定哪些成员为 public，哪些为 protected 和 private
        - 决定哪些类或函数要被声明成 friend

    - __什么是新类型的”未声明接口？（undeclared interface）“__
        - 对效率、异常安全性以及资源运用（如多任务锁和动态内存）提供何种保证？
        - 要在这些方面提供保证，需要在类中定义相应的约束条件。

    - __你的新类型有多么一般化？__
        - 即：是否需要定义一个模板类以支持不同类型？

    - __你真的需要一个新类型吗？__
        - 如果只是定义一个派生类，或者定义一个新的非成员函数或模板就能达到目的，就无需定义一个新类了。

---
### 20. 宁以 pass-by-reference-to-const 替换 pass-by-value

1. 当传值时，会调用对象的拷贝构造函数，函数结束时还会调用该对象的析构函数。而且一旦这个对象构成比较复杂，构造和析构的成本是很高的（会引发级联调用）。

2. 当传引用时，没有任何构造函数或析构函数被调用，没有任何新对象被创建。声明为 const 是为了实现与传值相同的效果——实参不会被更改。

3. 除了 __节省开销__，传引用还可以 __避免 _slicing_ （对象切割）问题__。假设一个 non-member 函数接受一个基类对象，而传入了一个派生类对象，这个派生类对象”特化“的那部分参数会被切割，在函数中调用这个对象的函数时，使用的仅是基类的版本。但是如果传引用，则不会发生这种问题。

4. 对于内置类型、STL的迭代器和函数对象，它们都非常小，有时候传值反而更高效，因为传引用的本质是传指针。

---
### 21. 必须返回对象时，别妄想返回其引用

1. __所谓 reference 只是个名称，代表某个既有对象。__ 任何时候看到一个 reference 声明，都应该立刻问自己：它的另一个名称是什么？

2. On the stack: __返回一个指向 local 对象的 reference，会导致未定义行为__。 因为该 local 对象（栈中的对象）在函数结束时已经被销毁，所以该 reference 是无意义的。
    ```cpp
    // 有理数乘法，一个典型的错误
    const Rational& operator* (const Rational& lhs, const Rational& rhs){
        Rational result(lhs.n * rhs.n, lhs.d * rhs.d);
        return result
    }
    ```

3. On the heap: 而如果是在堆中声明的对象，则可以解决这个问题，但是几乎必会导致内存泄漏：
    ```cpp
    // 更糟糕的写法
    const Rational& operator* (const Rational& lhs, const Rational& rhs){
        Rational* result = new Rational(lhs.n * rhs.n, lhs.d * rhs.d);
        returl *result;
    }

    // 当这样使用时：
    Rational w, x, y, z;
    w = x * y * z;
    ```
    这时执行了两次 * 操作，也就执行了两次 new，然而有一个中间结果却丢失了（y * z），这必会内存泄漏。

4. 因此，__就让它返回一个对象吧，绝不要返回一个指向 local stack对象的指针或引用，也不要返回一个指向 heap-allocated 的引用，也不要尝试返回一个指向 local static对象的指针或引用(这里特指当你同时需要多个这样的对象时)__，

---
### 22. 将成员变量声明为 private

1. 成员变量应该声明为 private（既不是 public，也不是 protected）. 这样不仅可以维护封装和访问的一致性（都用函数法访问）。

2. 还可以 __为”所有可能的实现“提供弹性__。例如 get()函数可以写成一种”懒方法“来实现，只有当get()被调用时才做计算，而不用一直维护一个计算好的结果，尤其是当对数据的访问不太频繁的时候。 再例如，可以使变量再被读写时可以通知其他对象、可以验证约束条件（例如由 setter 函数检查输入的值的范围）、可以在多线程环境中执行同步控制等等。。。

3. protected 也类似，因为 __protected 的封装性并不比 public 成员变量要高__。因为当我们使用一个 public 成员变量，而后删除了该变量，那么所有使用该变量的代码都要更改； 对于 protected，一旦一个 protected 变量被删除，所有使用该变量的派生类都要修改。

4. __从封装的角度来看，其实只有两种访问权限：private(提供封装)，和其他(不提供封装)__

---
### 23. 宁以 non-member、non-friend、替换 member 函数



