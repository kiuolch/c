# C++作业内容
*2.23 不能，因为如果指针p没有被初始化，则p存放的是一个随机的地址，无法判断其对象是否合法

*2.24 p合法是由于void 是一种特殊的指针类型，可以用于存放任意对象的地址。而指针lp为long类型，对象i为int类型，两者类型不一，指针要求两边类型严格一致，因此不合法

*2.25 
      
      1.ip是一个int类指针型的，i是一个int型的变量，r是一个int型的引用。
      
      2.i是一个int型的变量，ip是一个空指针。
      
      3.ip是一个int类型的指针，ip2是一个int类型的变量。
      
*2.35 j类型为int,&k类型为const int &,*p类型为const int *,j2类型为const int,&k2类型为const int &

*3.4

	//比较是否相同
	#include <iostream>
	#include <string>
	using namespace std;
	int main()
	{	
	    string str1 , str2;
	    cin>>str1>>str2;
	    if (str1 != str2)
	      {
		cout<<(str1 >= str2 ? str1 : str2)<<endl;
	      }
	}
	//比较长短
	#include <iostream>
	#include <string>
	using namespace std;
	int main()
	{	
		string str1 , str2;
		cin>>str1>>str2;
		if (str1.size() != str2.size())
		{
			cout<<(str1.size() >= str2.size() ?str1 :str2)<<endl;
		}
		else
		{
			cout<<"The length of these strings are the same!"<<endl;
		}	
	}

*3.5

	//字符串连接
	#include <iostream>
	#include <string>
	using namespace std;
	int main()
	{	
		string str1;
		string str2;
		while (getline(cin ,str1))
		{
			str2 += str1;
			cout<<str2<<endl;
		}		
	}	
	//带空格连接
	#include <iostream>
	#include <string>
	using namespace std;
	int main()
	{	
		string str1;
		string str2;
		while (getline(cin ,str1)
		{
			str2= str2+str1+" ";
			cout<<str2<<endl;
		}
	}

*3.20

	//相邻相加
	#include <iostream>
	#include <string>
	#include <vector>
	using namespace std;
	int main()
	{	
		vector<int> My_vector;
		int a[10];
		for (int i = 0;i<10;i++)
		{
			cin>>a[i];
		}
		for (int j = 0;j<10;j++)
		{
			My_vector.push_back(a[j]);
		}
		int sum[10];
		for (int k = 0;k<9;k++)
		{
			sum[k] = My_vector[k] + My_vector[k+1];
			cout<<sum[k]<<endl;
		}
	} 
	//首尾相加
	#include <iostream>
	#include <string>
	#include <vector>
	using namespace std;
	int main()
	{	
		vector<int> My_vector;
		int a[10];
		for (int i = 0;i<10;i++)
		{
			cin>>a[i];
		}
		for (int j = 0;j<10;j++)
		{
			My_vector.push_back(a[j]);
		}
		int sum[10];
		for (int k = 0;k<5;k++)
		{
			sum[k] = My_vector[k] + My_vector[9-k];
			cout<<sum[k]<<endl;
		}

	} 

*3.23

	#include <iostream>
	#include <string>
	#include <vector>
	using namespace std;
	void main()
	{	
		vector<int> text(10,5);
		for (auto it = text.begin(); it != text.end();it++) 
		{
			*it = *it * 2;
			cout<<*it<<endl;	
		}
	} 

*6.10

	#include <iostream>
	#include <string>
	#include <vector>
	using namespace std;

	int exchange(int &val1, int &val2)
	{
		int a;
		a = val1;
		val1 = val2;
		val2 = a;
		return 0;
	}
	int main()
	{	
		int val1,val2;
		cin>>val1>>val2;
		exchange(val1,val2);
		cout<<val1<<" "<<val2<<endl;
	}

*6.19 a不合法，原函数仅有一个参数，而a含有两个，bcd均合法

*6.39 a错误，参数int重复声明。b错误，未指定参数。c正确。

*7.16 没有限制。构造函数和一部分成员函数应该定义在public说明符之后，而数据成员和作为实现部分的函数则应该跟在private后面。

*7.27 

	class Screen
	{   
	public:
	    typedef std::string::size_type pos;
	//构造函数
	    Screen() = default;
	    Screen( const pos ht, const pos wt ) : height( ht ), width( wt ), contents( ht * wt, ' ' ) { }
	    Screen( const pos ht, const pos wt, const char c ) : height( ht ), width( wt ), contents( ht * wt, c ) { }
	public:
	//成员函数
	    Screen& cursor_move( const pos r, const pos c )
	    {
		cursor = r * width + c;
		return *this;
	    }
	    Screen& set_ch( const pos r, const pos c, const char ch )
	    {
		contents[ r * width + c ] = ch;
		return *this;
	    }
	    Screen& set_ch( const char ch )
	    {
		contents[ cursor ] = ch;
		return *this;
	    } 
	    Screen& display( void )
	    {
		std::cout << contents;
		return *this;
	    }

	private:
	//数据成员
	    std::string contents;
	    pos cursor = 0;
	    pos height = 0;
	    pos width = 0;
	};
	
  	
	
	#include<iostream>
	#include"Screen.h"

	using namespace std;

	int main()
	{
	    Screen myScreen( 5, 5, 'X' );
	    myScreen.cursor_move( 4, 0 ).set_ch( '#' ).display();
	    cout << "\n";
	    myScreen.display();
	    cout << "\n";

	    return 0;
	}

*7.49 a编译通过。b，c编译无法通过

*7.58 除了静态常量成员之外，其他静态成员不能在类的内部初始化.所以rate和vec不能在类内初始化，rate和vec的类外定义必须给出其初始值。

