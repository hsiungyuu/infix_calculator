# infix_calculator
---------------
## for homework
---------------
我不知道能說甚麼，反正就上課教的，哈哈。
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
