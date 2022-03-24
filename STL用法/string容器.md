# 1. 字符串的插入insert（）

insert() 函数可以在 string 字符串中指定的位置插入另一个字符串，它的一种原型为：

```c++
string& insert (size_t pos, const string& str);
```

pos 表示要插入的位置，也就是下标；str 表示要插入的字符串，它可以是 string 字符串，也可以是C风格的字符串。

请看下面代码：

```c++
#include <iostream>
#include <string>
using namespace std;

int main(){
    string s1, s2, s3;
    s1 = s2 = "1234567890";
    s3 = "aaa";
    s1.insert(5, s3);	//表示在下标为5的字符串s1后，插入字符串s3
    cout<< s1 <<endl;
    s2.insert(5, "bbb");
    cout<< s2 <<endl;
    return 0;
}
```

运行结果：
12345aaa67890
12345bbb67890



# 2. 删除字符串 erase（）

erase() 函数可以删除 string 中的一个子字符串。它的一种原型为：

```c++
string& erase (size_t pos = 0, size_t len = npos);
```

pos 表示要删除的子字符串的起始下标，len 表示要删除子字符串的长度。如果不指明 len 的话，那么直接删除从 pos 到字符串结束处的所有字符（此时 len = str.length - pos）。

请看下面的代码：

```c++
#include <iostream>
#include <string>
using namespace std;
int main(){
    string s1, s2, s3;
    s1 = s2 = s3 = "1234567890";
    s2.erase(5);
    s3.erase(5, 3);
    cout<< s1 <<endl;
    cout<< s2 <<endl;
    cout<< s3 <<endl;
    return 0;
}
```

运行结果：
1234567890
12345
1234590



# 3. 提取字符串 substr（）

substr() 函数用于从 string 字符串中提取子字符串，它的原型为：

```c++
string substr (size_t pos = 0, size_t len = npos) const;
```

pos 为要提取的子字符串的起始下标，len 为要提取的子字符串的长度。



请看下面的代码：

```c++
#include <iostream>
#include <string>
using namespace std;
int main(){
    string s1 = "first second third";
    string s2;
    s2 = s1.substr(6, 6);
    cout<< s1 <<endl;
    cout<< s2 <<endl;
    return 0;
}
```

运行结果：
first second third
second



# 4. 字符串查找 

1. **find() 函数**
   find() 函数用于在 string 字符串中查找子字符串出现的位置，它其中的两种原型为：

   ```c++
   size_t find (const string& str, size_t pos = 0) const;
   size_t find (const char* s, size_t pos = 0) const;
   ```

   第一个参数为待查找的子字符串，它可以是 string 字符串，也可以是C风格的字符串。第二个参数为开始查找的位置（下标）；如果不指明，则从第0个字符开始查找。
   

   请看下面的代码：

   ```c++
   #include <iostream>
   #include <string>
   using namespace std;
   int main(){
       string s1 = "first second third";
       string s2 = "second";
       int index = s1.find(s2,6);
       if(index < s1.length())
           cout<<"Found at index : "<< index <<endl;
       else
           cout<<"Not found"<<endl;
       return 0;
   }
   ```

   运行结果：
   Found at index : 6
   find() 函数最终返回的是子字符串第一次出现在字符串中的起始下标。本例最终是在下标6处找到了 s2 字符串。如果没有查找到子字符串，那么会返回 -1。

2. **rfind() 函数**
   rfind() 和 find() 很类似，同样是在字符串中查找子字符串，不同的是 find() 函数从第二个参数开始往后查找，而 rfind() 函数则最多查找到第二个参数处，如果到了第二个参数所指定的下标还没有找到子字符串，则 -1。

   ```c++
   #include <iostream>
   #include <string>
   using namespace std;
   int main(){
       string s1 = "first second third";
       string s2 = "second";
       int index = s1.rfind(s2,6);
       if(index < s1.length())
           cout<<"Found at index : "<< index <<endl;
       else
           cout<<"Not found"<<endl;
       return 0;
   }
   ```

   运行结果：
   Found at index : 6

3. **find_first_of() 函数**|
   find_first_of() 函数用于查找子字符串和字符串共同具有的字符在字符串中首次出现的位置。
   请看下面的代码：

   ```c++
   #include <iostream>
   #include <string>
   using namespace std;
   int main(){
       string s1 = "first second second third";
       string s2 = "asecond";
       int index = s1.find_first_of(s2);
       if(index < s1.length())
           cout<<"Found at index : "<< index <<endl;
       else
           cout<<"Not found"<<endl;
       return 0;
   }
   ```

   运行结果：
   Found at index : 3
   本例中 s1 和 s2 共同具有的字符是 ’s’，该字符在 s1 中首次出现的下标是3，故查找结果返回3。

# 5. 将字符串转化数字的一些函数

可以看一看这篇博客：https://blog.csdn.net/liu_feng_zi_/article/details/108045676?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_baidulandingword-0&spm=1001.2101.3001.4242

1. stoi()：将字符串转换为整型

   ```c++
   int n;
   string s1 = "9921";
   n = stoi(s1);	
   cout << n;	//结果n为9921的整型
   ```

2. stoll()：转换为long long

3. stof()：转换为float

4. stod()：转换为double

5. 将数字转换为字符串

   ```c++
   int i = 1023;
   string s = to_string(i);
   cout << s;	//结果s为1023的字符串类型
   ```

6. 字符大小写的转换

   ```c++
   //大写字母 + ' ' = 小写字母
   //小写字母 - ' ' = 大写字母
   char a = 'A';
   a = a + ' ';
   cout << a;
   ```

7. 单个字符转换为数字

   ```c++
   char a = '3';
   int i = 0;
   i = a - '0';
   //i == 3
   ```

   