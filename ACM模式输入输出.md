# 1. A+B问题I

- 题目描述
> 你的任务是计算a+b。

- 输入
> 输入包含一系列的a和b对，通过空格隔开。一对a和b占一行。

- 输出
> 对于输入的每对a和b，你需要依次输出a、b的和。  
> 如对于输入中的第二对a和b，在输出中它们的和应该也在第二行。

- 样例输入 复制
> 3 4  
> 11 40

- 样例输出 复制
> 7  
> 51  

```c++
#include<iostream>
using namespace std;
int main() {
    int a, b;
    while (cin >> a >> b) cout << a + b << endl;
}
```


# 2. A+B问题II
- 题目描述
> 计算a+b，但输入方式有所改变。

- 输入
> 第一行是一个整数N，表示后面会有N行a和b，通过空格隔开。

- 输出
> 对于输入的每对a和b，你需要在相应的行输出a、b的和。
> 如第二对a和b，对应的和也输出在第二行。

- 样例输入
> 2  
> 2 4  
> 9 21  

- 样例输出 复制
> 6  
> 30  

```c++
#include<iostream>
using namespace std;
int main() {
    int n, a, b;
    while (cin >> n) {
        while (n--) {
            cin >> a >> b;
            cout << a + b << endl;
        }
    }
}
```


# 3. A+B问题III
- 题目描述
> 你的任务依然是计算a+b。

- 输入
> 输入中每行是一对a和b。其中会有一对是0和0标志着输入结束，且这一对不要计算。

- 输出
> 对于输入的每对a和b，你需要在相应的行输出a、b的和。
> 如第二对a和b，他们的和也输出在第二行。

- 样例输入
> 2 4  
> 11 19  
> 0 0  

- 样例输出
> 6  
> 30  

```c++
#include<iostream>
using namespace std;
int main() {
    int a, b;
    while (cin >> a >> b) {
        if (a == 0 && b == 0) break;
        cout << a + b << endl;
    }
}
```


# 4. A+B问题IV
- 题目描述
> 你的任务是计算若干整数的和。

- 输入
> 每行的第一个数N，表示本行后面有N个数。
> 如果N=0时，表示输入结束，且这一行不要计算。

- 输出
> 对于每一行数据需要在相应的行输出和。

- 样例输入
> 4 1 2 3 4  
> 5 1 2 3 4 5  
> 0   

- 样例输出
> 10  
> 15  

```c++
#include<iostream>
using namespace std;
int main(){
    int n, a;
    while (cin >> n) {
        if (n == 0) break;
        int sum = 0;
        while (n--) {
            cin >> a;
            sum += a;
        }
        cout << sum << endl;
    }
}
```


# 5. A+B问题VII
- 题目描述
> 你的任务是计算两个整数的和。

- 输入
> 输入包含若干行，每行输入两个整数a和b，由空格分隔。

- 输出
> 对于每组输入，输出a和b的和，每行输出后接一个空行。

- 样例输入
> 2 4  
> 11 19  

- 样例输出
> 6  
>   
> 30  

```c++
#include<iostream>
using namespace std;
int main() {
    int a, b;
    while (cin >> a >> b) cout << a + b << endl << endl;
}
```


# 6. A+B问题VIII
- 题目描述
> 你的任务是计算若干整数的和。

- 输入
> 输入的第一行为一个整数N，接下来N行每行先输入一个整数M，然后在同一行内输入M个整数。

- 输出
> 对于每组输入，输出M个数的和，每组输出之间输出一个空行。

- 样例输入
> 3  
> 4 1 2 3 4  
> 5 1 2 3 4 5  
> 3 1 2 3  

- 样例输出
> 10  
>   
> 15  
>   
> 6  

```c++
#include<iostream>
using namespace std;
int main() {
    int n, a, b;
    while (cin >> n) {
        while (n--) {
            cin >> a;
            int sum = 0;
            while (a--) {
                cin >> b;
                sum += b;
            }
            cout << sum << endl;
            if (n != 0) cout << endl;
        }
    }
}
```


# 7. 平均绩点
- 题目描述
> 每门课的成绩分为A、B、C、D、F五个等级，为了计算平均绩点，规定A、B、C、D、F分别代表4分、3分、2分、1分、0分。

- 输入
> 有多组测试样例。每组输入数据占一行，由一个或多个大写字母组成，字母之间由空格分隔。

- 输出
> 每组输出结果占一行。如果输入的大写字母都在集合｛A,B,C,D,F｝中，则输出对应的平均绩点，结果保留两位小数。否则，输出“Unknown”。

- 样例输入
> A B C D F  
> B F F C C A  
> D C E F  

- 样例输出
> 2.00  
> 1.83  
> Unknown  

```c++
#include <iostream>
#include <stdio.h>
using namespace std;
int main() {
    string s;
    while (getline(cin, s)) { // 接受一整行字符串
        float sum = 0;
        int count = 0;
        int flag = 1;
        for (int i = 0; i < s.size(); i++) {
            if (s[i] == 'A') {sum += 4; count++;}
            else if (s[i] == 'B') {sum += 3; count++;}
            else if (s[i] == 'C') {sum += 2; count++;}
            else if (s[i] == 'D') {sum += 1; count++;}
            else if (s[i] == 'F') {sum += 0; count++;}
            else if (s[i] == ' ') continue;
            else {
                flag = 0;
                cout << "Unknown" << endl;
                break;
            }
        }
        if (flag) printf("%.2f\n", sum / count);
    }
    return 0;
}

```


# 8. 摆平积木
- 题目描述
> 小明很喜欢玩积木。一天，他把许多积木块组成了好多高度不同的堆，每一堆都是一个摞一个的形式。然而此时，他又想把这些积木堆变成高度相同的。但是他很懒，他想移动最少的积木块来实现这一目标，你能帮助他吗？

- 输入
> 输入包含多组测试样例。每组测试样例包含一个正整数n，表示小明已经堆好的积木堆的个数。  
> 接着下一行是n个正整数，表示每一个积木堆的高度h，每块积木高度为1。其中1<=n<=50,1<=h<=100。  
> 测试数据保证积木总数能被积木堆数整除。  
> 当n=0时，输入结束。  

- 输出
> 对于每一组数据，输出将积木堆变成相同高度需要移动的最少积木块的数量。
> 在每组输出结果的下面都输出一个空行。

- 样例输入
> 6  
> 5 2 4 1 7 5  
> 0  

- 样例输出
> 5  

```c++
#include<iostream>
#include<vector>
using namespace std;

int main() {
    int n;
    while (cin >> n) {
        if (n == 0) break;
        vector<int> nums = vector<int>(n, 0);
        int sum = 0;
        for (int i = 0; i < n; i++) {
            cin >> nums[i];
            sum += nums[i];
        }
        int average = sum / n;
        int result = 0;
        for (int i = 0; i < n; i++) {
            if ((nums[i] - average) > 0) result += (nums[i] - average);
        }
        cout << result << endl;
        cout<< endl;
    }
}
```


# 9. 奇怪的信
- 题目描述
> 有一天, 小明收到一张奇怪的信, 信上要小明计算出给定数各个位上数字为偶数的和。
> 例如：5548，结果为12，等于 4 + 8 。
> 小明很苦恼，想请你帮忙解决这个问题。

- 输入
> 输入数据有多组。每组占一行，只有一个整整数，保证数字在32位整型范围内。

- 输出
> 对于每组输入数据，输出一行，每组数据下方有一个空行。

- 样例输入
> 415326  
> 3262  

- 样例输出
> 12  
>   
> 10  


```c++
#include<iostream>
using namespace std; 
int main() {
    int n, a;
    while (cin >> n) {
        int result = 0;
        while (n != 0) {
            a = (n % 10);
            n = n / 10;
            if (a % 2 == 0) result += a;
        }
        cout << result << endl;
        cout << endl;
    }
}
```


# 运营商活动
- 题目描述
> 小明每天的话费是1元，运营商做活动，手机每充值K元就可以获赠1元，一开始小明充值M元，问最多可以用多少天？   
> 注意赠送的话费也可以参与到奖励规则中

- 输入
> 输入包括多个测试实例。每个测试实例包括2个整数M，K（2<=k<=M<=1000)。M=0，K=0代表输入结束。

- 输出
> 对于每个测试实例输出一个整数，表示M元可以用的天数。

- 样例输入
> 2 2  
> 4 3  
> 13 3  
> 0 0  

- 样例输出
> 3  
> 5  
> 19  

```c++
#include<iostream>
using namespace std;
int main() {
    int m, k;
    while (cin >> m >> k) {
        if (m == 0 && k == 0) break;
        int sum = m + m / k; // 第一轮回得到总话费
        int count = m / k + m % k; // 额外话费 = 赠送+剩余话费 
        while (count / k != 0) { // 只要额外话费大于 k 就还能获得 剩余话费  
            sum += count / k;
            count = count / k + count % k;
        }
        cout << sum << endl;
    }
}
```


# 11. 共同祖先
- 题目描述
> 小明发现和小宇有共同祖先！现在小明想知道小宇是他的长辈，晚辈，还是兄弟。

- 输入
> 输入包含多组测试数据。每组首先输入一个整数N（N<=10），接下来N行，每行输入两个整数a和b，表示a的父亲是b（1<=a,b<=20）。小明的编号为1，小宇的编号为2。
> 输入数据保证每个人只有一个父亲。

- 输出
> 对于每组输入，如果小宇是小明的晚辈，则输出“You are my younger”，如果小宇是小明的长辈，则输出“You are my elder”，如果是同辈则输出“You are my brother”。

- 样例输入
> 5  
> 1 3  
> 2 4  
> 3 5  
> 4 6  
> 5 6  
> 6  
> 1 3  
> 2 4  
> 3 5  
> 4 6  
> 5 7  
> 6 7  

- 样例输出
> You are my elder  
> You are my brother  

```c++
#include<iostream>
#include<vector>
using namespace std;
int main() {
    int n, a, b;
    vector<int> nums = vector<int>(30, 0); // 使用数组来记录映射关系，初始化为0
    while (cin >> n) {
        while (n--) {
            cin >> a >> b;
            nums[a] = b; // 记录映射关系
        }
        int len_ming = 0, len_yu = 0;
        int ming = nums[1];// 小明编号为1 
        while (ming != 0) { // 当ming 为0 的时候，说明找到了祖先了 
            ming = nums[ming];
            len_ming++; // 记录小明找到祖先的长度
        }
        int yu = nums[2]; // 与小明同理
        while (yu != 0) {
            yu = nums[yu];
            len_yu++;
        }
        if (len_ming > len_yu) cout << "You are my elder" << endl;
        else if (len_ming == len_yu) cout << "You are my brother" << endl;
        else cout << "You are my younger" << endl;
    }
}
```


# 12. 打印数字图形
- 题目描述
> 先要求你从键盘输入一个整数n（1<=n<=9），打印出指定的数字图形。

- 输入
> 输入包含多组测试数据。每组输入一个整数n（1<=n<=9）。

- 输出
> 对于每组输入，输出指定的数字图形。
> 注意：每行最后一个数字后没有任何字符。

- 样例输入
> 5

- 样例输出

```
    1  
   121  
  12321  
 1234321  
123454321  
 1234321  
  12321  
   121  
    1  
```

```c++
#include<iostream>
#include<vector>
using namespace std;

void printTopPart(int n) {
    for (int i = 1; i <= n; i++) {
        // 打印空格
        for (int j = 1; j <= n - i; ++j) {
            cout << " ";
        }

        // 打印递增数字
        for (int j = 1; j <= i; j++) {
            cout << j;
        }

        // 打印递减数字
        for (int j = i - 1; j >= 1; j--) {
            cout << j;
        }
        cout << endl;
    }
}

void printBottomPart(int n) {
    for (int i = n - 1; i >= 1; i--) {
        // 打印空格
        for (int j = 1; j <= n - i; j++) {
            cout << " ";
        }
        // 打印递增数字
        for (int j = 1; j <= i; j++) {
            cout << j;
        }

        // 打印递减数字
        for (int j = i - 1; j >= 1; j--) {
            std::cout << j;
        }
        cout << endl;
    }
}
int main() {
    int n;
    while (cin >> n) {
        if (n < 1 || n > 9) {
            cout << "输入的整数n超出范围" << endl;
        }
        printTopPart(n);
        printBottomPart(n);
    }
}
```


# 13. 镂空三角形
- 题目描述
> 把一个字符三角形掏空，就能节省材料成本，减轻重量，但关键是为了追求另一种视觉效果。在设计的过程中，需要给出各种花纹的材料和大小尺寸的三角形样板，通过电脑临时做出来，以便看看效果。

- 输入
> 每行包含一个字符和一个整数n(0<n<41)，不同的字符表示不同的花纹，整数n表示等腰三角形的高。显然其底边长为2n-1。如果遇到@字符，则表示所做出来的样板三角形已经够了。

- 输出
> 每个样板三角形之间应空上一行，三角形的中间为空。行末没有多余的空格。每条结果后需要再多输出一个空行。

- 样例输入
> X 2  
> A 7  
> @  

- 样例输出

```
 X
XXX

      A
     A A
    A   A
   A     A
  A       A
 A         A
AAAAAAAAAAAAA
```

```C++
#include <iostream>
#include <string>
using namespace std;

// 分为三部分打印：根据规律
void myprint(char c, int n){
    // 第一部分：第一行
    cout << string(n- 1, ' ') << c << endl;
    
    // 第二部分：中间部分
    for(int i = n - 2, j = 1; i >= 1; i--, j += 2){
        cout << string(i, ' ') << c << string(j, ' ') << c << endl;
    }
    
    // 第三部分：最后一行
    if(n > 1)
        cout << string(n + n - 1, c) << endl;
    cout << endl;
}

int main() {
    char c;
    int n;
    while(cin >> c){
        if(c == '@')
            break;
        cin >> n;
        myprint(c, n);
    }
    return 0;
}
```


# 14.句子缩写
- 题目描述
> 输出一个词组中每个单词的首字母的大写组合。

- 输入
> 输入的第一行是一个整数n，表示一共有n组测试数据。（输入只有一个n，没有多组n的输入）  
> 接下来有n行，每组测试数据占一行，每行有一个词组，每个词组由一个或多个单词组成；每组的单词个数不超过10个，每个单词有一个或多个大写或小写字母组成；  
> 单词长度不超过10，由一个或多个空格分隔这些单词。  

- 输出
> 请为每组测试数据输出规定的缩写，每组输出占一行。

- 样例输入
> 1  
> ad dfa     fgs  

- 样例输出
> ADF

```c++
#include<iostream>
#include<string>
using namespace std;
char changeChar(char & a) { // 小写变大写
    if (a >= 'a' && a <= 'z') a -= 32;
    return a;
}
int main() {
    int n;
    string result, s;
    cin >> n;
    getchar(); // 吸收一个回车，因为输入n之后，要输入一个回车
    while (n--) {
        result = "";
        getline(cin, s);
        result += changeChar(s[0]);
        for (int i = 1; i < s.size() - 1; i++) { // 单词之间可能有多个空格
            if (s[i] == ' ' && s[i + 1] != ' ') result += changeChar(s[i + 1]);
        }
        cout << result << endl;
    }
}
```


# 15. 神秘字符
- 题目描述
> 考古学家发现墓碑上有神秘的字符。经过仔细研究，发现原来这是开启古墓入口的方法。  
> 墓碑上有2行字符串，其中第一个串的长度为偶数，现在要求把第2个串插入到第一个串的正中央，如此便能开启墓碑进入墓中。

- 输入
> 输入数据首先给出一个整数n，表示测试数据的组数。（整个输入中，只有一个n）
然后是n组数据，每组数据2行，每行一个字符串，长度大于0，小于50，并且第一个串的长度必为偶数。

- 输出
> 请为每组数据输出一个能开启古墓的字符串，每组输出占一行。

- 样例输入
> 2  
> asdf  
> yu  
> rtyu  
> HJK  

- 样例输出
> asyudf  
> rtHJKyu

```c++
#include<iostream>
#include<string>
using namespace std;
int main() {
    int n;
    cin >> n;
    getchar(); // 吸收n后的一个回车
    while (n--) {
        string s, t;
        cin >> s >> t;

        string result = "";
        for (int i = 0; i < s.size() / 2; i++) { // 处理s的前半段
            result += s[i];
        }
        result += t; // 添加 字符串t
        for (int i = s.size() / 2; i < s.size(); i++) { // 处理s的后半段
            result += s[i];
        }
        cout << result << endl;
    }
}
```


# 16. 位置互换
- 题目描述
> 给定一个长度为偶数位的字符串，请编程实现字符串的奇偶位互换。

- 输入
> 输入包含多组测试数据。  
> 输入的第一行是一个整数n，表示有测试数据。（整个输入中，只有一个n）  
> 接下来是n组测试数据，保证串长为偶数位(串长<=50)。  

- 输出
> 请为每组测试数据输出奇偶位互换后的结果，每组输出占一行。  

- 样例输入
> 2  
> 0aa0  
> bb00  

- 样例输出
> a00a  
> bb00  

```c++
#include<iostream>
#include<string>
using namespace std;
void swap(char &a, char &b) { // 交换两个字符串
    char tmp = a;
    a = b;
    b = tmp;
}
int main() {
    int n;
    cin >> n;
    string s;
    while (n--) {
        cin >> s;
        for (int i = 0; i < s.size() - 1; i += 2) { // 在s字符串上原地修改
            swap(s[i], s[i + 1]);
        }
        cout << s << endl;
    }
}
```


# 17. 出栈合法性
- 题目描述
> 已知自然数1，2，...，N（1<=N<=100）依次入栈，请问序列C1，C2，...，CN是否为合法的出栈序列。

- 输入
> 输入包含多组测试数据。  
> 每组测试数据的第一行为整数N（1<=N<=100），当N=0时，输入结束。  
> 第二行为N个正整数，以空格隔开，为出栈序列。

- 输出
> 对于每组输入，输出结果为一行字符串。
> 如给出的序列是合法的出栈序列，则输出Yes，否则输出No。

- 样例输入
```
5
3 4 2 1 5
5
3 5 1 4 2
0
```

- 样例输出
> Yes  
> No  

```c++
#include<iostream>
#include<stack>
#include<vector>
using namespace std;
int main() {
    int n;
    int nums[105];
    while(cin >> n) {
        if (n == 0) break;
        for (int index = 0; index < n; index++) cin >> nums[index]; // 输入数组
        stack<int> st;
        int index = 0;
        for (int i = 1; i <= n; i++) { // 判断出栈合法性
            st.push(i);
            while (!st.empty() && st.top() == nums[index]) {
                st.pop();
                index++;
            }
        }
        if (st.empty() && index == n) cout << "Yes" << endl;
        else cout << "No" << endl;
    }
}
```


# 18. 链表的基本操作
- 题目描述
> 本题考察链表的基本操作。

- 输入
> 输入数据只有一组，第一行有n+1个整数，第一个整数是这行余下的整数数目n，后面是n个整数。  
> 这一行整数是用来初始化列表的，并且输入的顺序与列表中的顺序相反，也就是说如果列表中是1、2、3那么输入的顺序是3、2、1。  
> 第二行有一个整数m，代表下面还有m行。每行有一个字符串，字符串是“get”，“insert”，“delete”，“show”中的一种。  
> 如果是“get”，代表获得第a个元素。（a从1开始计数）  
> 如果是“delete”，代表删除第a个元素。（a从1开始计数）  
> 如果是“insert”，则其后跟着两个整数a和e，代表在第a个位置前面插入e。（a从1开始计数）  
> “show”之后没有正数，直接打印链表全部内容。  

- 输出
> 如果获取成功，则输出该元素；  
> 如果删除成功，则输出“delete OK”；  
> 如果获取失败，则输出“get fail”  
> 如果删除失败，则输出“delete fail”  
> 如果插入成功，则输出“insert OK”，否则输出“insert fail”。  
> 如果是“show”，则输出列表中的所有元素，如果列表是空的，则输出“Link list is empty”  
> 注：所有的双引号均不输出。

- 样例输入

```
3 3 2 1
21
show
delete 1
show
delete 2
show
delete 1
show
delete 2
insert 2 5
show
insert 1 5
show
insert 1 7
show
insert 2 5
show
insert 3 6
show
insert 1 8
show
get 2
```

- 样例输出

```
1 2 3
delete OK
2 3
delete OK
2
delete OK
Link list is empty
delete fail
insert fail
Link list is empty
insert OK
5
insert OK
7 5
insert OK
7 5 5
insert OK
7 5 6 5
insert OK
8 7 5 6 5
7
```

```c++
#include<iostream>
using namespace std;
// 定义链表节点结构体
struct LinkedNode {
    int val;
    LinkedNode* next;
    LinkedNode(int val):val(val), next(nullptr){}
};

int _size = 0;
LinkedNode* _dummyHead =  new LinkedNode(0); // 这里定义的头结点 是一个虚拟头结点，而不是真正的链表头结点

// 获取到第index个节点数值，如果index是非法数值直接返回-1， 注意index是从0开始的，第0个节点就是头结点
int get(int index) {
    if (index > (_size - 1) || index < 0) {
        return -1;
    }
    LinkedNode* cur = _dummyHead->next;
    while(index--){ // 如果--index 就会陷入死循环
        cur = cur->next;
    }
    return cur->val;
}

// 在链表最前面插入一个节点，插入完成后，新插入的节点为链表的新的头结点
void addAtHead(int val) {
    LinkedNode* newNode = new LinkedNode(val);
    newNode->next = _dummyHead->next;
    _dummyHead->next = newNode;
    _size++;
}

// 在链表最后面添加一个节点
void addAtTail(int val) {
    LinkedNode* newNode = new LinkedNode(val);
    LinkedNode* cur = _dummyHead;
    while(cur->next != nullptr){
        cur = cur->next;
    }
    cur->next = newNode;
    _size++;
}

// 在第index个节点之前插入一个新节点，例如index为0，那么新插入的节点为链表的新头节点。
// 如果index 等于链表的长度，则说明是新插入的节点为链表的尾结点
// 如果index大于链表的长度，则返回空
// 如果index小于0，则在头部插入节点
int addAtIndex(int index, int val) {

    if(index > _size) return -1;
    if(index < 0) return -1;
    LinkedNode* newNode = new LinkedNode(val);
    LinkedNode* cur = _dummyHead;
    while(index--) {
        cur = cur->next;
    }
    newNode->next = cur->next;
    cur->next = newNode;
    _size++;
    return 0;
}

// 删除第index个节点，如果index 大于等于链表的长度，直接return，注意index是从0开始的
int deleteAtIndex(int index) {
    if (index >= _size || index < 0) {
        return -1;
    }
    LinkedNode* cur = _dummyHead;
    while(index--) {
        cur = cur ->next;
    }
    LinkedNode* tmp = cur->next;
    cur->next = cur->next->next;
    delete tmp;
    //delete命令指示释放了tmp指针原本所指的那部分内存，
    //被delete后的指针tmp的值（地址）并非就是NULL，而是随机值。也就是被delete后，
    //如果不再加上一句tmp=nullptr,tmp会成为乱指的野指针
    //如果之后的程序不小心使用了tmp，会指向难以预想的内存空间
    tmp=nullptr;
    _size--;
    return 0;
}

// 打印链表
int printLinkedList() {
    LinkedNode* cur = _dummyHead;
    if (cur->next == nullptr) return -1;
    while (cur->next != nullptr) {
        cout << cur->next->val << " ";
        cur = cur->next;
    }
    cout << endl;
    return 0;
}

int main() {
    int n, a, m, t, z;
    string s;
    cin >> n;
    LinkedNode* head = nullptr;
    while (n--) {
        cin >> a;
        addAtHead(a);
    }
    cin >> m;
    while (m--) {
        cin >> s;
        if (s == "show")  {
            if (printLinkedList() == -1) cout << "Link list is empty" << endl;
        }
        if (s == "delete") {
            cin >> t; 
            // 本题的删除索引是从1开始，函数实现是从0开始，所以这里是 t - 1
            if (deleteAtIndex(t - 1) == -1) cout << "delete fail" << endl; 
            else cout << "delete OK" << endl;
        }
        if (s == "insert") {
            cin >> t >> z; 
            if (addAtIndex(t - 1, z) == -1) cout << "insert fail" << endl;
            else cout << "insert OK" << endl;

        }
        if (s == "get") {
            cin >> t;
            int getValue = get(t - 1);
            if (getValue == -1) cout << "get fail" << endl;
            else cout << getValue << endl;
        }
    }
}
```


# 19. 单链表反转
- 题目描述
> 根据一个整数序列构造一个单链表，然后将其反转。  
> 例如：原单链表为 2 3 4 5 ，反转之后为5 4 3 2

- 输入
> 输入包括多组测试数据，每组测试数据占一行，第一个为大于等于0的整数n，表示该单链表的长度，后面跟着n个整数，表示链表的每一个元素。整数之间用空格隔开

- 输出
> 针对每组测试数据，输出包括两行，分别是反转前和反转后的链表元素，用空格隔开  
> 如果链表为空，则只输出一行，list is empty  

- 样例输入
> 5 1 2 3 4 5   
> 0  

- 样例输出
> 1 2 3 4 5   
> 5 4 3 2 1   
> list is empty  

```c++
#include<iostream>
using namespace std;
// 定义链表节点结构体
struct LinkedNode {
    int val;
    LinkedNode* next;
    LinkedNode(int val):val(val), next(nullptr){}
};

LinkedNode* reverseList(LinkedNode* head) {
    LinkedNode* temp; // 保存cur的下一个节点
    LinkedNode* cur = head;
    LinkedNode* pre = NULL;
    while(cur) {
        temp = cur->next;  // 保存一下 cur的下一个节点，因为接下来要改变cur->next
        cur->next = pre; // 翻转操作
        // 更新pre 和 cur指针
        pre = cur;
        cur = temp;
    }
    return pre;
}

void printLinkedList(LinkedNode* head) {
    LinkedNode* cur = head;
    while (cur != nullptr) {
        cout << cur->val << " ";
        cur = cur->next;
    }
    cout << endl;
}

int main() {

        int n, m;
        LinkedNode* dummyHead =  new LinkedNode(0); // 这里定义的头结点 是一个虚拟头结点，而不是真正的链表头结点
        while (cin >> n) {
            if (n == 0) {
                cout << "list is empty" << endl;
                continue;
            }
            LinkedNode* cur = dummyHead;
            while (n--) {
                cin >> m;
                LinkedNode* newNode = new LinkedNode(m); // 开始构造节点
                cur->next = newNode;
                cur = cur->next;
            }
            printLinkedList(dummyHead->next);
            printLinkedList(reverseList(dummyHead->next));
        }
}
```


# 20. 删除重复元素
- 题目描述
> 根据一个递增的整数序列构造有序单链表，删除其中的重复元素

- 输入
> 输入包括多组测试数据，每组测试数据占一行，第一个为大于等于0的整数n，表示该单链表的长度，后面跟着n个整数，表示链表的每一个元素。整数之间用空格隔开

- 输出
> 针对每组测试数据，输出包括两行，分别是删除前和删除后的链表元素，用空格隔开  
> 如果链表为空，则只输出一行，list is empty

- 样例输入
```
5 1 2 3 4 5
5 1 1 2 2 3
0
```

- 样例输出
```
1 2 3 4 5 
1 2 3 4 5 
1 1 2 2 3 
1 2 3 
list is empty
```


```c++
#include<iostream>
using namespace std;
// 定义链表节点结构体
struct LinkedNode {
    int val;
    LinkedNode* next;
    LinkedNode(int val):val(val), next(nullptr){}
};

void printLinkedList(LinkedNode* head) {
    LinkedNode* cur = head;
    while (cur != nullptr) {
        cout << cur->val << " ";
        cur = cur->next;
    }
    cout << endl;
}

// 过滤掉重复元素输出
void printLinkedListV(LinkedNode* head) {
    LinkedNode* cur = head;
    int lastA, lastB;
    while (cur != nullptr && cur->next != nullptr) { 
        if (cur->val != cur->next->val) cout << cur->val << " ";
        cur = cur->next;
    }
    cout << cur->val << " ";
    cout << endl;
}

int main() {

        int n, m;
        LinkedNode* dummyHead =  new LinkedNode(0); // 这里定义的头结点 是一个虚拟头结点，而不是真正的链表头结点
        while (cin >> n) {
            if (n == 0) {
                cout << "list is empty" << endl;
                continue;
            }
            LinkedNode* cur = dummyHead;
            while (n--) {
                cin >> m;
                LinkedNode* newNode = new LinkedNode(m);
                cur->next = newNode;
                cur = cur->next;
            }
            printLinkedList(dummyHead->next);
            printLinkedListV(dummyHead->next);
        }
}
```


# 21. 构造二叉树
- 题目描述
> 给你一棵二叉树的前序遍历和中序遍历结果，要求你写出这棵二叉树的后序遍历结果。

- 输入
> 输入包含多组测试数据。每组输入包含两个字符串，分别表示二叉树的前序遍历和中序遍历结果。每个字符串由不重复的大写字母组成。

- 输出
> 对于每组输入，输出对应的二叉树的后续遍历结果。

- 样例输入
```
DBACEGF ABCDEFG
BCAD CBAD
```


- 样例输出
```
ACBFGED
CDAB
```

```c++
#include <iostream>
#include <unordered_map>
#include <string>
using namespace std;

// 定义二叉树节点结构
struct TreeNode {
    char val;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int val) : val(val), left(nullptr), right(nullptr) {}
};

TreeNode* buildTreeRecursive(string& preorder, string& inorder,
                             int preStart, int inStart, int inEnd,
                             unordered_map<int, int>& indexMap) {
    if (preStart > preorder.size() - 1 || inStart > inEnd) {
        return nullptr;
    }

    // 根据前序遍历结果获取当前子树的根节点值
    char rootValue = preorder[preStart];
    TreeNode* root = new TreeNode(rootValue);

    // 根据中序遍历结果获取当前子树的根节点在中序遍历中的索引
    int rootIndex = indexMap[rootValue];

    // 递归构造左子树和右子树
    root->left = buildTreeRecursive(preorder, inorder, preStart + 1, inStart, rootIndex - 1, indexMap);
    root->right = buildTreeRecursive(preorder, inorder, preStart + rootIndex - inStart + 1, rootIndex + 1, inEnd, indexMap);

    return root;
}

// 根据前序遍历和中序遍历结果构造二叉树
TreeNode* buildTree(string& preorder, string& inorder) {
    // 创建一个哈希表，用于快速查找中序遍历结果中节点值对应的索引
    std::unordered_map<int, int> indexMap;
    for (int i = 0; i < inorder.size(); ++i) {
        indexMap[inorder[i]] = i;
    }

    // 递归构造二叉树
    return buildTreeRecursive(preorder, inorder, 0, 0, inorder.size() - 1, indexMap);
}
// 后序遍历二叉树
void postorderTraversal(TreeNode* root) {
    if (root == nullptr) {
        return;
    }

    postorderTraversal(root->left);
    postorderTraversal(root->right);
    cout << root->val;
}

int main() {

    string s;
    while (getline(cin, s)) { // 接受一整行字符串
        string preorder = "", inorder = "";
        // 拆分出两个字符串
        int i;
        for (i = 0; s[i] != ' '; i++) preorder += s[i];  
        i++;
        for (; i < s.size(); i++) inorder += s[i]; 

        // 开始构造二叉树
        TreeNode* root = buildTree(preorder, inorder);
        postorderTraversal(root);
        cout << endl;
    }
    return 0;
}
```


# 22. 二叉树的遍历
- 题目描述
> 给出一个n个节点的二叉树，请求出二叉树的前序遍历，中序遍历和后序遍历。

- 输入
> 第一位一个整数n(0<n<=26)，表示二叉树有n个节点，以下n行，每行第一个为一个大写字母表示节点，后面为两整数，第一个表示左儿子序号，第二个表示右儿子序号，如果该序号为0表示没有。 (例如下面示例中，F序号为1，C序号为2，E序号为3，A序号为4，D序号为5，G序号为6，B序号为7)

- 输出
> 共三行，第一行为二叉树的前序遍历，第二行为中序遍历，第三行为后序遍历

- 样例输入
```
7
F 2 3
C 4 5
E 0 6
A 0 0
D 7 0
G 0 0
B 0 0
```

- 样例输出
```
FCADBEG
ACBDFEG
ABDCGEF
```

```c++
#include <iostream>
#include <unordered_map>
#include <vector>
using namespace std;

struct TreeNode {
    char val;
    TreeNode* left;
    TreeNode* right;
    TreeNode(char val) : val(val), left(nullptr), right(nullptr) {}
};

// 根据输入数据构造二叉树
TreeNode* buildTree(unordered_map<char, pair<char, char>>& nodeMap, char rootValue) {
    if (rootValue == '0') {
        return nullptr;
    }

    TreeNode* root = new TreeNode(rootValue);
    int leftChild = nodeMap[rootValue].first;
    int rightChild = nodeMap[rootValue].second;

    root->left = buildTree(nodeMap, leftChild);
    root->right = buildTree(nodeMap, rightChild);

    return root;
}

// 前序遍历二叉树
void preorderTraversal(TreeNode* root) {
    if (root == nullptr) {
        return;
    }

    cout << root->val;
    preorderTraversal(root->left);
    preorderTraversal(root->right);
}

// 中序遍历二叉树
void inorderTraversal(TreeNode* root) {
    if (root == nullptr) {
        return;
    }

    inorderTraversal(root->left);
    cout << root->val;
    inorderTraversal(root->right);
}

// 后序遍历二叉树
void postorderTraversal(TreeNode* root) {
    if (root == nullptr) {
        return;
    }

    postorderTraversal(root->left);
    postorderTraversal(root->right);
    cout << root->val;
}

int main() {
    int n;
    cin >> n;
    unordered_map<char, std::pair<char, char>> nodeMap;

    // 先保存输入的数据 
    vector<char> index = vector<char>(n + 1, '0'); 
    vector<vector<int>> nums = vector<vector<int>>(n + 1, vector<int>(2, 0));
    for (int i = 1; i <= n; i++) {
        cin >> index[i] >> nums[i][0] >> nums[i][1];
    }

    // 生成二叉树 
    for (int i = 1; i <= n; i++) {
        nodeMap[index[i]] = make_pair(index[nums[i][0]], index[nums[i][1]]);
    }
    TreeNode* root = buildTree(nodeMap, index[1]);

    preorderTraversal(root);
    cout << std::endl;

    inorderTraversal(root);
    cout << std::endl;

    postorderTraversal(root);
    cout << std::endl;

    return 0;
}
```


# 23. 二叉树的高度
- 题目描述
> 现给定一棵二叉树的先序遍历序列和中序遍历序列，要求你计算该二叉树的高度。

- 输入
> 输入包含多组测试数据，每组输入首先给出正整数N（<=50），为树中结点总数。下面2行先后给出先序和中序遍历序列，均是长度为N的不包含重复英文字母（区别大小写）的字符串。

- 输出
> 对于每组输入，输出一个整数，即该二叉树的高度。

- 样例输入
```
9
ABDFGHIEC
FDHGIBEAC
7
Abcdefg
gfedcbA
```

- 样例输出
```
5
7
```

```c++
#include <iostream>
#include <string>
#include <unordered_map>
using namespace std;

struct TreeNode {
    char val;
    TreeNode* left;
    TreeNode* right;
    TreeNode(char val) : val(val), left(nullptr), right(nullptr) {}
};

// 根据先序遍历和中序遍历序列构造二叉树
TreeNode* buildTree(string& preorder, string& inorder,
                    int preStart, int inStart, int inEnd,
                    unordered_map<char, int>& indexMap) {
    if (preStart > preorder.size() - 1 || inStart > inEnd) {
        return nullptr;
    }

    char rootValue = preorder[preStart];
    TreeNode* root = new TreeNode(rootValue);
    int rootIndex = indexMap[rootValue];

    root->left = buildTree(preorder, inorder, preStart + 1, inStart, rootIndex - 1, indexMap);
    root->right = buildTree(preorder, inorder, preStart + rootIndex - inStart + 1, rootIndex + 1, inEnd, indexMap);

    return root;
}

// 计算二叉树的高度
int getHeight(TreeNode* root) {
    if (root == nullptr) {
        return 0;
    }

    int leftHeight = getHeight(root->left);
    int rightHeight = getHeight(root->right);

    return max(leftHeight, rightHeight) + 1;
}

int main() {
    int n;
    while (cin >> n) {
        string preorder, inorder;
        cin >> preorder >> inorder;

        unordered_map<char, int> indexMap;
        for (int i = 0; i < n; ++i) {
            indexMap[inorder[i]] = i;
        }

        TreeNode* root = buildTree(preorder, inorder, 0, 0, n - 1, indexMap);
        int height = getHeight(root);

        cout << height << endl;
    }
    return 0;
}
```


# 24.  最长公共子序列
- 题目描述
> 给你一个序列X和另一个序列Z，当Z中的所有元素都在X中存在，并且在X中的下标顺序是严格递增的，那么就把Z叫做X的子序列。  
> 例如：Z=<a,b,f,c>是序列X=<a,b,c,f,b,c>的一个子序列，Z中的元素在X中的下标序列为<1,2,4,6>。  
> 现给你两个序列X和Y，请问它们的最长公共子序列的长度是多少？

- 输入
> 输入包含多组测试数据。每组输入占一行，为两个字符串，由若干个空格分隔。每个字符串的长度不超过100。

- 输出
> 对于每组输入，输出两个字符串的最长公共子序列的长度。

- 样例输入
```
abcfbc abfcab
programming contest 
abcd mnp
```

- 样例输出
```
4
2
0
```

```c++
#include <iostream>
#include <vector>
#include <string>
using namespace std;
int main() {
    string text1, text2;
    while (cin >> text1 >> text2) {
         vector<vector<int>> dp(text1.size() + 1, vector<int>(text2.size() + 1, 0));
        for (int i = 1; i <= text1.size(); i++) {
            for (int j = 1; j <= text2.size(); j++) {
                if (text1[i - 1] == text2[j - 1]) {
                    dp[i][j] = dp[i - 1][j - 1] + 1;
                } else {
                    dp[i][j] = max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }
        cout << dp[text1.size()][text2.size()] << endl;
    }
    return 0;
}
```


# 25. 最爱的城市
- 题目描述
> 一天小明捧着一本世界地图在看，突然小明拿起笔，将他最爱的那些城市标记出来，并且随机的将这些城市中的某些用线段两两连接起来。  
> 小明量出了每条线段的长度，现在小明想知道在这些线段组成的图中任意两个城市之间的最短距离是多少。

- 输入
> 输入包含多组测试数据。  
> 每组输入第一行为两个正整数n（n<=10）和m（m<=n*(n-1)/2），n表示城市个数，m表示线段个数。  
> 接下来m行，每行输入三个整数a，b和l，表示a市与b市之间存在一条线段，线段长度为l。（a与b不同）  
> 每组最后一行输入两个整数x和y，表示问题：x市与y市之间的最短距离是多少。（x与y不同）  
> 城市标号为1~n，l<=20。

- 输出
> 对于每组输入，输出x市与y市之间的最短距离，如果x市与y市之间非连通，则输出“No path”。

- 样例输入
```
4 4
1 2 4
1 3 1
1 4 1
2 3 1
2 4
```


- 样例输出
```
3
```

```c++
// dijkstra求最短路
#include <bits/stdc++.h>
using namespace std;

const int inf = 0x3f3f3f3f;

int main() {
    int n, m;
    while (cin >> n >> m) {
        // 建图
        vector<vector<int>> g(n + 1, vector<int>(n + 1, inf));
        for (int i = 0; i < m; ++i) {
            int a, b, w;
            cin >> a >> b >> w;
            g[a][b] = min(g[a][b], w);
            g[b][a] = min(g[b][a], w);
        }
        
        int x, y;
        cin >> x >> y;
        
        vector<int> dist(n + 1, inf); // dist[i]: x->i的最短距离
        dist[x] = 0;
        vector<int> st(n + 1); // st[i]: dist[i]是否已经确定
        while (1) {
            // 找出还未确定最短路的点里面，距离x最近的点t
            int t = -1;
            for (int i = 1; i <= n; ++i) {
                if (!st[i] && (t == -1 || dist[i] < dist[t])) {
                    t = i;
                }
            }
            
            // 非连通或找到x->y的最短路了
            if (t == -1 || dist[t] == inf || st[t] || t == y) { 
                break;
            }
            st[t] = true;
            
            for (int i = 1; i <= n; ++i) {
                // 用dist[t]更新s到其它点的距离
                if (!st[i]) dist[i] = min(dist[i], dist[t] + g[t][i]);
            }
        }
        if (dist[y] >= inf) cout << "No path" << endl;
        else cout << dist[y] << endl;
    }
    
    return 0;
}
```















