string使用注意事项

```
① 初始化 char c[100][100]
不能使用方法：char c[100][100] = {'0'}
应该：for(int i=0;i<100;i++)
		for(int j=0;j<100;j++)
			c[i][j] = '0'

② string s
  s.size()返回字符串长度；
  
  s[s.size()]的值为'\0'
  
③ 字符组成字符串
  string s="";
  char c[100];
  for(int i=0;i<100;i++)
  	 s.push_back(c[i])

④ string 本身反转：
string s;
s.reverse(s.begin(), s.end())

⑤ string 复制：
string a,b;
a.assign(b.rbegin(),b.rend());//将b逆序赋值给a

⑥ 截取子串
string a,b;
b=a.substr(pos,len);//从字符串a的pos位置开始(包括pos位置)，正序截取len个字符，赋值给b
//例如 b=a.substr(0,5); 注意string的第一个字符的下标是0

⑦
   string &operator=(const string &s); 把字符串s赋给当前字符串
　　string &assign(const char *s);      用c类型字符串s赋值
　　string &assign(const char *s,int n);用c字符串s开始的n个字符赋值
　　string &assign(const string &s);    把字符串s赋给当前字符串
　　string &assign(int n,char c);       用n个字符c赋值给当前字符串
　　string &assign(const string &s,int start,int n);把字符串s中从start开始的n个字符赋给当前字符串
　　string &assign(const_iterator first,const_itertor last);把first和last迭代器之间的部分赋给字符串
```

