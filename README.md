# C++作业内容
*2.23 不能，因为如果指针p没有被初始化，则p存放的是一个随机的地址，无法判断其对象是否合法

*2.24 p合法是由于void 是一种特殊的指针类型，可以用于存放任意对象的地址。而指针lp为long类型，对象i为int类型，两者类型不一，指针要求两边类型严格一致，因此不合法

*2.25 1.ip是一个int类指针型的，i是一个int型的变量，r是一个int型的引用。
      2.i是一个int型的变量，ip是一个空指针。
      3.ip是一个int类型的指针，ip2是一个int类型的变量。
      
*2.35 j类型为int,&k类型为const int &,*p类型为const int *,j2类型为const int,&k2类型为const int &

*3.4
	
	#include <iostream>
	#include <string>
        using namespace std;
        void main()
	{	
	string str1 , str2;
	cin>>str1>>str2;
	if (str1 != str2)
	    {
		cout<<(str1 >= str2 ? str1 : str2)<<endl;
	    }
      	}

