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

*8.4  

	#include "stdafx.h"
	#include <iostream>
	#include <string>
	#include <fstream>
	#include <vector>
	using namespace std;

	void readFunc(const string filename, vector<string>& vec)
	{
		ifstream in(filename);
		string s;
		while ( getline(in, s) )
		{
			vec.push_back(s);
		}
	}

	int main(int argc, char *argv[])
	{
		string filename = "G:/testt.txt";
		vector<string> strVec;
		readFunc(filename, strVec);

		system("pause");
	}
 
*8.7
 
	 int main(int argc, char** argv)
	{
		ifstream ifs(argv[1]);
		ofstream ofs(argv[2]);

		if (ifs) 
		{
			CSales_data total;
			if (read(ifs, total)) 
			{
				CSales_data trans;
				while (read(ifs, trans)) 
				{
					if (total.isbn() == trans.isbn()) 
					{
						total.combine(trans);
					}
					else 
					{
						print(ofs, total) << endl;
						total = trans;
					}
				}
				print(ofs, total) << endl;
			}
			else 
			{
				cout << "No data?" << endl;
			}
		}
		else {
			cout << "file name error?" << endl;
		}
		return 0;
	}
	
*8.9

	#include "stdafx.h"
	#include <iostream>
	#include <string>
	#include <fstream>
	#include <vector>
	#include <sstream>
	using namespace std;

	istream& streamFunc(istream& in)
	{
		string s;
		while (in >> s)
		{
			cout << s << " ";
		}
		cout << endl;
		in.clear();
		return in;
	}

	int main(int argc, char** argv)
	{
		string s = "123456";
		istringstream record(s);
		streamFunc(record);

		system("pause");
		return 0;
	}
	
*9.11

	vector<int> vec;    // 0
	vector<int> vec(10);    // 0
	vector<int> vec(10,1);  // 1
	vector<int> vec{1,2,3,4,5}; // 1,2,3,4,5
	vector<int> vec(other_vec); // same as other_vec
	vector<int> vec(other_vec.begin(), other_vec.end()); // same as other_vec
	
*9.25

相等：不发生删除操作

elem2为尾后迭代器：删除elem1到最后一个元素

皆为尾后迭代器：不发生删除操作

*9.29 resize(100)会将其大小改为100个元素的大小，添加新元素并初始化，之后使用resize(10)会将之后的90个元素舍弃。

*9.43 

	#include<iostream>
	#include<fstream>
	#include<sstream>
	#include<string>
	#include<vector>
	#include<forward_list>
	using namespace std;

	void func(string &s, string &oldVal, string &newVal)
	{
		int _size = oldVal.size();
		string::iterator it1 = s.begin();
		string::iterator it2 = newVal.begin();
		string::iterator it3 = newVal.end();

		 for (it1; it1 <= (s.end()-oldVal.size()+1); ++it1)
		{
			//pos可以由两个迭代器相减得到,返回截取到的string
			if((s.substr(it1-s.begin(),_size) == oldVal))//substr()的作用就是截取string中的一段
			{
				it1 = s.erase(it1,it1+_size);//返回的是最后一个被删除的元素之后的位置
				it1 = s.insert(it1, it2, it3);//VS2010运行出错，但是未找到原因何在，本质上说应该是没有错误的
				advance(it1,_size);//向前一定大小
			}
		}
	}

	int main(int argc, char**argv)
	{
		string s = "abcdefg";
		string oldval = "bc";
		string newval = "asas";
		func(s,oldval,newval);
		cout<<s<<endl;
		return 0;
	}

改进：

	#include<iostream>  
	#include<fstream>  
	#include<sstream>  
	#include<string>  
	#include<vector>  
	#include<forward_list>  
	using namespace std;  

	void func(string &s, string &oldVal, string &newVal)  
	{  
		int _size = oldVal.size(); 
		int _size1 = newVal.size();
		string::iterator it1 = s.begin();  
		string::iterator it2 = newVal.begin();  
		string::iterator it3 = newVal.end();  

		for (it1; it1 <= (s.end()-oldVal.size()+1); ++it1)  
		{  
			//pos可以由两个迭代器相减得到,返回截取到的string  
			if((s.substr(it1-s.begin(),_size) == oldVal))//substr()的作用就是截取string中的一段  
			{  
				it1 = s.erase(it1,it1+_size);//返回的是最后一个被删除的元素之后的位置  
				s.insert(it1, it2,it3);//原因在于insert()函数返回了指向第一个插入字符的迭代器，而我将其直接赋值给it1，从const转为非const，类型不同，产生错误  
				//test code
				/*cout<<(it1-s.begin())<<endl;
				cout<<s<<endl;*/
				advance(it1,_size1-1);//向前_size1-1大小，目的是为了让it1仍然指向当前字符串的首位置，因为前面进行了++it1
			}  
		}  
	}  

	int main(int argc, char**argv)  
	{  
		string s = "abcdefg";  
		string oldval = "bc";  
		string newval = "asas";  
		func(s,oldval,newval);  
		cout<<s<<endl;  
		system("pause");
		return 0;  
	}  
	
*9.52

	#include<iostream>
	#include<string>
	#include<vector>
	#include<stack>
	using namespace std;
	unsigned priority(char a)
	{
		if (a == '?')
			return 0;
		if (a == '+' || a == '-')
			return 1;
		if (a == '*' || a == '/')
			return 2;
		if (a == '(' || a == ')')
			return 3;
	}

	int main(int argc, char** argv)
	{
		string a = "(8+15*4+5-6/3+4)*25";
		stack<char>op;
		string op_type{ "+-*/()"};
		string data_temp="";
		if (a[0] == '+' || a[0] == '-' )
		{
			a = '0' + a;
		}
		for (auto i : a)
		{
			   if (op_type.find(i)==op_type.npos)
			   {
				   data_temp += i;
			   }
			   else
			   {
				   cout << data_temp;
				   data_temp = "";
				   if(!op.empty())
				   { 
				     while (!op.empty()&&priority(i) <= priority(op.top()))
				     {
						   cout << op.top();
						   op.pop();
				     }
				     op.push(i);
				   }
				   else
					 op.push(i);
				   if (op.top() == '(')
					   op.top() = '?';
				   if (op.top() == ')')
				   {
					   op.pop();
					   while (op.top() != '?')
					   {
						   cout << op.top();
						   op.pop();
					   }
					   op.pop();
				   }
			   }
		}
		if(!op.empty())
		{
			cout << data_temp;
			while(!op.empty())
			{ 
			cout << op.top();
			op.pop();
			}
		}

		return 0;

	}
	
*10.3

	#include<iostream>
	#include<string>
	#include<vector>
	#include<algorithm>
	#include<numeric>
	using namespace std;

	int main(int argc, char**argv)
	{
		int a[10] = {0,1,2,5,4,5,4,5,4,5};
		vector<int> vec(a,a+10);
		cout<<"元素之和为："<<accumulate(vec.begin(),vec.end(),0);

		return 0;
	}

*10.15

	[a](int &b){cout<<a+b;}	
	
*10.34

	#include<vector>  
	#include<algorithm>  
	#include<numeric>  
	#include<functional>
	#include<iterator>
	using namespace std;
	using namespace placeholders;//占位符的命名空间

	int main(int argc, char**argv)  
	{  
		int a[5] = {1,2,3,4,5};
		vector<int> day1(a,a+5);

		for (auto it1 = day1.rbegin(); it1 != day1.rend() ; ++it1)//这里的++实际上是递减的
		{
			cout<<*it1<<" ";
		}

		return 0;  
	} 

*11.12

	#include<iostream>  
	#include<string>  
	#include<fstream>
	#include<list>
	#include<vector> 
	#include<map>  
	#include<set>
	#include<cctype>//ctype无法打开，包含tolower()函数和ispunct函数
	#include<algorithm>
	#include<utility>//保存pair的头文件
	using namespace std;

	int main(int argc, char**argv)  
	{ 
		vector<pair<string,int>> vec1(12);//事先定义大小，或者使用push_back()
		ifstream in1("1.txt");
		string str;
		size_t i = 0;
		while (in1>>str)
		{
			vec1[i].first = str;
			++i;
		}
		ifstream in2("2.txt");
		int val;
		size_t j = 0;
		while (in2>>val)
		{
			vec1[j].second = val;
			++j;
		}

		vector<pair<string,int>>::iterator it1 = vec1.begin();
		cout<<"vector中元素为："<<endl;
		for (it1; it1 != vec1.end(); ++it1)
		{
			cout<<it1->first<<" "<<it1->second<<endl;
		}

		return 0;  
	}  
	
*11.17 第三个back_inserter()需要使用push_back()，而set不能够使用push_back()，其余均合法

*11.38

	#include <unordered_map>
	#include <set>
	#include <string>
	#include <iostream>
	#include <fstream>
	#include <sstream>

	using std::string;

	void wordCounting()
	{
	    std::unordered_map<string, size_t> word_count;
	    for (string word; std::cin >> word; ++word_count[word])
		;
	    for (const auto& w : word_count)
		std::cout << w.first << " occurs " << w.second
			  << (w.second > 1 ? "times" : "time") << std::endl;
	}

	void wordTransformation()
	{
	    std::ifstream ifs_map("../data/word_transformation.txt"),
		ifs_content("../data/given_to_transform.txt");
	    if (!ifs_map || !ifs_content) {
		std::cerr << "can't find the documents." << std::endl;
		return;
	    }

	    std::unordered_map<string, string> trans_map;
	    for (string key, value; ifs_map >> key && getline(ifs_map, value);)
		if (value.size() > 1)
		    trans_map[key] =
			value.substr(1).substr(0, value.find_last_not_of(' '));

	    for (string text, word; getline(ifs_content, text); std::cout << std::endl)
		for (std::istringstream iss(text); iss >> word;) {
		    auto map_it = trans_map.find(word);
		    std::cout << (map_it == trans_map.cend() ? word : map_it->second)
			      << " ";
		}
	}

	int main()
	{
	    // wordCounting();
	    wordTransformation();
	}

*12.1 b1和b2都包含4个元素。

*12.10 正确

*12.15  直接将删除器函数修改即可

	[](connection *p){ disconnect *p; }
	
*12.17

(a)：不合法，ix不是new返回的指针

(b)：同上

(c)：合法，unique_ptr必须采用直接初始化

(d)：不合法，同(a)

(e)：合法

(f)：不合法，必须使用new返回的指针进行初始化，赋值和拷贝的操作也不包含get()方法。

*12.18 release()函数的作用就是放弃对指针指向对象的控制权，但shared_ptr是多对一的关系，其他的智能指针仍然可以删除这个对象，所以这个函数的话对shared_ptr没意义

*12.19 

	shared_ptr<int> u(new int(1024));
	weak_ptr<int> w_ptr(u);
	if (shared_ptr<int> u = w_ptr.lock())
	{
		//....
	}

*12.30 
 
        //主函数.cpp 
	#include "Chapter12.h"
	#include <iostream>
	using namespace std;

	void runQueries(std::ifstream& infile)
	{
		TextQuery tq(infile);
		while (true) {
		cout << "enter word to look for, or q to quit: ";
		string s;
		if (!(cin >> s) || s == "q") break;
		print(cout, tq.query(s)) << endl;
		}
	}

	int main()
	{
		ifstream file("1.txt");
		runQueries(file);
	}
	


        //头文件.h
	#ifndef Cccc//第一次包含本头文件时，#ifndef判断为真，预处理器将处理后面的内容直到#endif，此时的预处理变量Cccc已定义
	#define Cccc//第二次包含本头文件时，#ifndef判断为假，预处理器将忽略后面的内容

	#include <string>
	#include <fstream>
	#include <map>
	#include <set>
	#include <vector>
	#include <iostream>
	#include <sstream>
	using namespace std;

	class QueryResult;
	class TextQuery {
	public:
		using LineNo = vector<string>::size_type;
		TextQuery(std::ifstream&);
		QueryResult query(const string&) const;

	private:
		shared_ptr<vector<string>> input;
		std::map<string, shared_ptr<std::set<LineNo>>> result;
	};

	class QueryResult {
	public:
		friend std::ostream& print(std::ostream&, const QueryResult&);

	public:
		QueryResult(const string& s, shared_ptr<std::set<TextQuery::LineNo>> set,
			shared_ptr<vector<string>> v)
			: word(s), nos(set), input(v)
		{
		}

	private:
		string word;
		shared_ptr<std::set<TextQuery::LineNo>> nos;
		shared_ptr<vector<string>> input;
	};

	std::ostream& print(std::ostream&, const QueryResult&);

	TextQuery::TextQuery(std::ifstream& ifs) : input(new vector<string>)
	{
		LineNo lineNo{0};
		for (string line; std::getline(ifs, line); ++lineNo) {
			input->push_back(line);
			std::istringstream line_stream(line);
			for (string text, word; line_stream >> text; word.clear()) {
				// avoid read a word followed by punctuation(such as: word, )
				std::remove_copy_if(text.begin(), text.end(),
					std::back_inserter(word), ispunct);
				// use reference avoid count of shared_ptr add.
				auto& nos = result[word];
				if (!nos) nos.reset(new std::set<LineNo>);
				nos->insert(lineNo);
			}
		}
	}

	QueryResult TextQuery::query(const string& str) const
	{
		// use static just allocate once.
		static shared_ptr<std::set<LineNo>> nodate(new std::set<LineNo>);
		auto found = result.find(str);
		if (found == result.end())
			return QueryResult(str, nodate, input);
		else
			return QueryResult(str, found->second, input);
	}

	std::ostream& print(std::ostream& out, const QueryResult& qr)
	{
		out << qr.word << " occurs " << qr.nos->size()
			<< (qr.nos->size() > 1 ? " times" : " time") << std::endl;
		for (auto i : *qr.nos)
			out << "\t(line " << i + 1 << ") " << qr.input->at(i) << std::endl;
		return out;
	}
	#endif//只要简单的加上就好了，无视C++中的作用域规则,作用是防止头文件被重复包含

*13.12 析构函数执行三次：accum，item1，item2

*13.18

	#include<iostream>  
	#include<string>  
	#include<fstream>
	#include<list>
	#include<vector> 
	#include<map>  
	#include<set>
	#include<cctype>//ctype无法打开，包含tolower()函数和ispunct函数
	#include<algorithm>
	#include<utility>//保存pair的头文件
	#include<memory>
	using namespace std;

	//具体操作时将类的声明置于头文件中
	class Employee
	{
	public:
		Employee();//默认构造函数
		Employee(string& s);//接受一个string的构造函数	
		Employee(const Employee&) =delete;//不需要拷贝构造函数，怎么可能有人一样。将其声明为 =delete
		Employee& operator= (const Employee&) =delete;
		int number(){return _number;}
	private:
		string employee;
		int _number;
		static int O_number;//static静态成员数据在类内声明，但只可以在类外定义，在类外定义时可不加static
	};

	int Employee::O_number = 0;
	Employee::Employee()//默认构造函数
	{
		_number = O_number++;
	}
	Employee::Employee(string& s)//接受一个string的构造函数
	{
		employee = s;
		_number = O_number++;
	}

	void show(Employee a)
	{
		cout<<a.number()<<endl;
	}
	int main(int argc, char**argv)  
	{
		Employee a, b, c;
		show(a);//调用函数时需要拷贝一次
		show(b);
		show(c);

		return 0;
	} 

*13.46

(a)：f()为函数的返回值，临时值，属于右值，&&

(b)：vi[0]为变量，属于左值，&

(c)：r1为变量，属于左值，&

(d)：右侧为表达式，属于右值，&&

*13.49

	StrVec::StrVec(StrVec&& s) {
		auto newData = alloc.allocate(s.size());
		auto dest = newData;
		auto last = uninitialized_copy(std::move(s.elements),std::move(s.first_free),dest);
	    elements = dest;
	    first_free = last;
	    cap = first_free;
	    s.elements = s.first_free = s.cap = nullptr;
	}

	StrVec& StrVec::operator=(StrVec&& s) {
		if(this != &s) {
			free();
			elements = s.elements;
			first_free = s.first_free;
			cap = s.cap;
			s.elements = s.first_free = s.cap = nullptr;
		}
	}
	String::String(String&& s) {
		auto newData = alloc.allocate(s.length());
		auto last = uninitialized_copy(std::move(s.elements),std::move(s.end),newData);
		elements = newData;
		end = last;
		s.elements = s.end = nullptr;
	}
	String& String::operator=(String&& s) {
		if(this != &s) {
			free();
			elements = s.elements;
			end = s.end;
			s.elements = s.end = nullptr;
		}
	}
	Message::Message(Message&& m):contents(std::move(m.contents)) {
		remove_folders(m);
	}
	Message& Message::operator=(Message&& m) {
		if(this != &m) {
			remove_from_Folders();
			contents = std::move(m.contents);
			folders = std::move(m.folders);
			add_to_Folders(m);
		}
		return *this;
	}
	void Message::remove_folders(Message* m) {
		folders = std::move(m->folders);
		for(auto f : folders) {
			f->remMsg(m);
			f->addMsg(this);
		}
		m->folders.clear();
	}
	
*13.58
 
	#include <vector>
	#include <iostream>
	#include <algorithm>

	using std::vector;
	using std::sort;

	class Foo {
	public:
		Foo sorted()&&;
		Foo sorted() const&;

	private:
		vector<int> data;
	};

	Foo Foo::sorted() &&
	{
		sort(data.begin(), data.end());
		std::cout << "&&" << std::endl; // debug
		return *this;
	}

	Foo Foo::sorted() const &
	{
		//    Foo ret(*this);
		//    sort(ret.data.begin(), ret.data.end());
		//    return ret;

		std::cout << "const &" << std::endl; // debug

		//    Foo ret(*this);
		//    ret.sorted();     //13.56
		//    return ret;

		return Foo(*this).sorted(); //13.57
	}

	int main()
	{
		Foo().sorted(); // call "&&"
		Foo f;
		f.sorted(); // call "const &"
	}
	
*14.3 (a) 都不是 (b)string (c) vector (d) string

*14.20 

	class Sales_data
	{
		friend Sales_data operator+(const Sales_data &lhs, const Sales_data &rhs);
	public:
		Sales_data& operator+=(const Sales_data &rhs);
		//其他成员
	};
	Sales_data operator+(const Sales_data &lhs, const Sales_data &rhs)
	{
		Sales_data sum = lhs;
		sum += rhs;
		return sum;
	}
	Sales_data& Sales_data::operator+=(const Sales_data &rhs)
	{
		units_sold += rhs.units_sold;
		revenue += rhs.revenue;
		return *this;
	}
	
*14.38

	#include <iostream>
	#include <vector>
	#include <string>
	#include <algorithm>
	using std::istream;
	using std::cout;
	using std::cin;
	using std::endl;
	using std::vector;
	using std::string;

	class StrLenIs
	{
	public:
		StrLenIs(int len) : len(len) { }
		bool operator()(const string &str) { return str.length() == len; }

	private:
		int len;
	};

	void readStr(istream &is, vector<string> &vec)
	{
		string word;
		while (is >> word)
		{
			vec.push_back(word);
		}
	}

	int main()
	{
		vector<string> vec;
		readStr(cin, vec);
		const int minLen = 1;
		const int maxLen = 10;
		for (int i = minLen; i <= maxLen; ++i)
		{
			StrLenIs slenIs(i);
			cout << "len: " << i << ", cnt: " << count_if(vec.begin(), vec.end(), slenIs) << endl;
		}

		return 0;
	}
	
*14.52

	struct longDouble {
		//用于演示的成员operator+; 在通常情况下+s是个非成员
		longDouble operator+(const SmallInt&);
		//其他成员与14.9.2节一致
	};
	longDouble operator+(longDouble&, double);
	SmallInt si;
	longDouble ld;
	ld = si + ld;
	ld = ld + si;
	
对于ld=si+ld，由于LongDouble不能转换为SmallInt，因此Smallint的成员operator+和friend operator都不可行。

由于Smallint不能转换为LongDouble，LongDouble的成员operator+和非成员operator+也都不可行。

由于SmallInt可以转换为int， LongDouble了可以转换为float和double，所以内置的operator+(int, float)和operator+(int, double)都可行，会产生二义性。

对于ld=ld+si，类似上一个加法表达式，由于Smallint不能转换为double，LongDouble也不能转换为SmallInt，因此SmallInt的成员operator+和两个非成员operator+都不匹配。

LongDouble的成员operator+可行，且为精确匹配。

SmallInt可以转换为int，longDouble可以转换为float和double，因此内置的operator+(float, int)和operator(double, int)都可行。但它们都需要类型转换，因此LongDouble的成员operator+优先匹配。

*15.12  有必要，override是表示对其基类函数的覆盖，final是表示此函数不能再被其他的函数所覆盖

*15.16 

	class limit_quote : public Disc_quote
	{
	public:
		limit_quote();//默认构造函数
		limit_quote(const string&book, double price, size_t qty,double disc):Disc_quote(book,price,qty,disc){}//构造函数,直接调用基类的构造函数
		double net_price(size_t n) const
		{
			if (n > quantity)
			{
				return quantity*(1-_discount)*price+(n-quantity)*price;
			} 
			else
			{
				return quantity*(1-_discount)*price;
			}
		}
	};

*15.30

	class Basket
	{
	public:
		void add_item(const std::shared_ptr<Quote> &sale) { items.insert(sale); }
		double total_receipt(std::ostream&) const;
	private:
		static bool compare(const std::shared_ptr<Quote> &lhs, const std::shared_ptr<Quote> &rhs)
		{
			return lhs->isbn() < rhs->isbn();
		}
		std::multiset<std::shared_ptr<Quote>, decltype(compare)*> items{compare};
	};

	double Basket::total_receipt(ostream &os) const
	{
		double sum = 0.0;
		for(auto iter = items.cbegin(); iter != items.cend(); iter = items.upper_bound(*iter))
		{
			sum += print_total(os, **iter, items.count(*iter));
		}
		os << "Total Sale: " << sum << endl;
		return sum;
	}
	
*16.11 在List类内，使用模版名不需要再加参数列表，而ListItem使用时必须加上<>模版参数列表

*16.19 

        //.h
	#ifndef HAVE_H
	#define HAVE_H

	template <typename T> void Have(T &t)
	{
		for (size_t i = 0; i < t.size(); ++i)
		{
			cout<<t[i]<<endl;
		}
	}
	#endif HAVE_H
	

	//.cpp
	#include <iostream>
	#include <vector>
	#include <list>
	#include <string>
	#include "Have.h"
	using namespace std;

	int main(int argc,char** argv)
	{
		vector<int> vec1;
		vec1.push_back(2);
		vec1.push_back(3);
		Have(vec1);
		system("pause");
		return 0;
	}

*16.41

	//.h
	#ifndef REU_TYPE_H
	#define REU_TYPE_H

	template <typename T> auto sum(const T&a,const T&b) ->decltype(a+b)//将函数的返回类型指定为a+b的类型
	{
		return a+b;
	}
	#endif REU_TYPE_H
	

	//.cpp
	#ifndef REU_TYPE_H
	#define REU_TYPE_H

	template <typename T> auto sum(const T&a,const T&b) ->decltype(a+b)//将函数的返回类型指定为a+b的类型
	{
		return a+b;
	}
	#endif REU_TYPE_H

*16.62

	//Scales_data.h
	#include <iostream>  
	#include <string>  
	class Sales_data  
	{  
	    std::string bookNo;  
	    unsigned units_sold;  
	    double revenue;  
	    double avg_price()const { return units_sold ? revenue / units_sold : 0; }  
	public:  
	    Sales_data(const std::string &s=std::string(), unsigned n = 0, double p = 0) :bookNo(s), units_sold(n), revenue(p) {}  
	    Sales_data(std::istream &is);  
	    std::string isbn()const { return bookNo; }  
	    Sales_data &operator+=(const Sales_data &s);  
	    friend std::hash<Sales_data>;  
	    friend std::ostream &operator<<(std::ostream &os, const Sales_data &s);  
	    friend std::istream &operator>>(std::istream &is, Sales_data &s);  
	    friend bool operator==(const Sales_data &ls, const Sales_data &rs);  
	    friend Sales_data operator+(const Sales_data &ls, const Sales_data &rs);  
	    friend std::ostream &print(std::ostream &os, const Sales_data &s);  
	    friend std::istream &read(std::istream &is, Sales_data &s);  
	};  
	bool operator!=(const Sales_data &ls, const Sales_data &rs);  
	Sales_data add(const Sales_data &ls, const Sales_data &rs);  

	namespace std  
	{  
	    template<> struct hash<Sales_data>  
	    {  
		typedef size_t result_type;  
		typedef Sales_data argument_type;  
		size_t operator()(const Sales_data &s)const {  
		    return hash<string>()(s.bookNo) ^ hash<unsigned>()(s.units_sold) ^ hash<double>()(s.revenue);  
		}  
	    };  
	}
	

	//Scales_data.cpp
	#include "Sales_data.h"  

	Sales_data::Sales_data(std::istream &is)  
	{  
	    is >> *this;  
	}  

	Sales_data &Sales_data::operator+=(const Sales_data &s)  
	{  
	    units_sold += s.units_sold;  
	    revenue += s.revenue;  
	    return *this;  
	}  

	std::ostream &operator<<(std::ostream &os, const Sales_data &s)  
	{  
	    os << s.isbn() << " " << s.units_sold << " " << s.revenue << " " << s.avg_price();  
	    return os;  
	}  

	std::istream &operator>>(std::istream &is, Sales_data &s)  
	{  
	    double price;  
	    is >> s.bookNo >> s.units_sold >> price;  
	    if (is)  
		s.revenue = s.units_sold*price;  
	    else  
		s = Sales_data();  
	    return is;  
	}  

	bool operator==(const Sales_data &ls, const Sales_data &rs)  
	{  
	    return ls.bookNo == rs.bookNo&&ls.units_sold == rs.units_sold&&ls.revenue == rs.revenue;  
	}  
	bool operator!=(const Sales_data &ls, const Sales_data &rs)  
	{  
	    return !(ls == rs);  
	}  

	Sales_data operator+(const Sales_data &ls, const Sales_data &rs)  
	{  
	    Sales_data temp = ls;  
	    temp += rs;  
	    return temp;  
	}  

	Sales_data add(const Sales_data &ls, const Sales_data &rs)  
	{  
	    Sales_data temp = ls;  
	    temp += rs;  
	    return temp;  
	}  

	std::ostream &print(std::ostream &os, const Sales_data &s)  
	{  
	    os << s.isbn() << " " << s.units_sold << " " << s.revenue << " " << s.avg_price();  
	    return os;  
	}  

	std::istream &read(std::istream &is, Sales_data &s)  
	{  
	    double price;  
	    is >> s.bookNo >> s.units_sold >> price;  
	    s.revenue = s.units_sold*price;  
	    return is;  
	}  
	
	
	//main.cpp
	#include <memory>  
	#include <unordered_set>  
	#include "Sales_data.h"  

	int main()  
	{  
	    //! test for ex16.62  
	    std::unordered_multiset<Sales_data> mset;  
	    Sales_data sd("Bible", 10, 0.98);  

	    mset.emplace(sd);  
	    mset.emplace("C++ Primer", 5, 9.99);  

	    for (const auto &item : mset)  
		std::cout << "the hash code of " << item.isbn()  
		<< ":\n0x" << std::hex << std::hash<Sales_data>()(item)  
		<< "\n";  
	    system("pause");  
	    return 0;  
	}  
