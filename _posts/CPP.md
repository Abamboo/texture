# CPP

## 2 变量和基本类型

### 2.3 复合类型

#### 引用

1. 引用只是别名

2. 示例

   int vial = 1024;
   int &refval = vial;
   cout << vial << endl;
   refval = 2;
   cout << vial << endl;

   结果

   ![image-20200911112904138](C:\Users\1116\AppData\Roaming\Typora\typora-user-images\image-20200911112904138.png)

#### 指针

```
//指针
	int a = 1, *pa = &a;
	int b = 2;
	int *pb=0;//初始化，但没有指向认可对象

	cout << *pa << endl;//1

	pa = &b;//pa指向b，a的值并没有改变
	cout << *pa << endl;//2
	cout << b<<" "<< a << endl;//2 1

	*pa = 3;//b的值被改变，指针pa并没有变化
	cout << *pa << endl;//3
	cout << b << " " << a << endl;//3 1
	pa = 0;//pa不指向任何对象
	//cout << *pa << endl;//引发异常
	cout << pa << endl;
	cout << b << " " << a << endl;
```

![](C:\Users\1116\AppData\Roaming\Typora\typora-user-images\image-20200913105541156.png)

**指针和引用区别**

指针本身时对象，可以赋值拷贝，可以重新绑定到另外对象；引用不是一个对象，无法重新绑定到另外的对象；指针无需有初值，引用必须在定义时赋值。

指向指针的指针

指向指针的引用

**智能指针**

智能指针也是模板，在创建智能指针时，必须提供额外的信息-指针可以指向的类型

处理资源泄露问题、处理悬空指针

shared_ptr:

unique_ptr:

## 8.3 string流

istringstream从string读取数据，ostringstream向string写入数据，而头文件stringstream既可以从string读数据也可以向string写数据。

## 继承

单继承

多继承

菱形继承

## 长度那些事

**length()**

函数，在c++中只用来获取字符串的长度

**size()**

函数，在获取字符串长度时，与length()作用相同

除此之外，还可以获取vector等STL容器的长度

**sizeof()**

运算符，用来计算对象所占内存空间的大小

代码示例

```
int main() {
	string str = "abcdefg";
	cout << str.length() << endl;//7
	cout << str.size() << endl;//7

	//sizeof
	int a;
	cout << sizeof(a) << endl;//4
	int *b;
	cout << sizeof(b) << endl;//8

	cout << sizeof(int)<<" "//4
		<< sizeof(char) << " "//1
		<< sizeof(long) << " "//4
		<< sizeof(double) << " "//8
		<< sizeof(float) << " "//4
		<< sizeof(int*) << " "//8
		<< sizeof(char*) << " "//8
		<< sizeof(long*) << " "//8
		<< sizeof(float*) << " "//8
		<< endl;

	int c[] = { 1,2,3,4,5 };
	cout << sizeof(c)<< endl;//20
	return 0;
}
```

**capacity**()

容量函数，STL中容器使用，获取当前能够容纳的元素数量

```
vector<int> res(5,0);
	cout << res.capacity() <<endl;//5
	res.push_back(1);
	res.push_back(2);
	res.push_back(3);
	res.push_back(4);
	res.push_back(5);
	cout << res.capacity() << endl;//10
	res.push_back(6);
	cout << res.capacity() << endl;//15
```

