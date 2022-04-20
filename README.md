# infix_calculator
---------------
## for homework
---------------
我不知道能說甚麼，反正就上課教的，但這是我的寫法<br>
下面是輸入後序求值。
--------------
```cpp

#include <iostream>
#include <string>
#include <stack>

using namespace std;

int main() {
	ios::sync_with_stdio(0);cin.tie(0);
	int buffer1, buffer2;
	stack <int> numbers;
	string expn;
	while (cin >> expn)
		if (isdigit(expn[0]) || (expn.size() > 1))
			numbers.push(stoi(expn));
		else {
			buffer2 = numbers.top(); numbers.pop();
			buffer1 = numbers.top(); numbers.pop();
			switch (expn[0]) {
			case '+':
				numbers.push(buffer1 + buffer2);
				break;
			case '-':
				numbers.push(buffer1 - buffer2);
				break;
			case '*':
				numbers.push(buffer1 * buffer2);
				break;
			case '/':
				numbers.push(buffer1 / buffer2);
				break;
			}
		}
	cout << numbers.top() << '\n';
}

```

-----------------------
## 這是中序轉後序
```cpp
#include <iostream>
#include <string>

using namespace std;

#define Priority(x) (x == '+' || x == '-' ? 1 : x == '%' ? 2 : (x == '*' || x == '/' ? 3 : 0))

int main() {
	ios::sync_with_stdio(0);cin.tie(0);
	char operators[1000];
	string expn;
	int ptr = 0;
	getline(cin, expn);
	for(int i = 0; i != expn.size(); ++i)
		if(expn[i] != ' ') {
			if(isalpha(expn[i]))
				cout << expn[i] << ' ';
			else if(expn[i] == '(')
				operators[ptr] = '(', ++ptr;
			else if(expn[i] == ')') {
				while(operators[ptr - 1] != '(')
					--ptr, cout << operators[ptr] << ' ';
				--ptr;
			}
			else{
				while(ptr && Priority(operators[ptr - 1]) >= Priority(expn[i]))
					--ptr, cout << operators[ptr] << ' ';
				operators[ptr] = expn[i]; ++ptr;
			}
		}
	while(ptr)
		--ptr, cout << operators[ptr] << ' ';
	cout << '\n';
	return 0;
}


```
