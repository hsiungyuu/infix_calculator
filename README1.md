#輸入中序->輸出後序
---------------
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
	while(getline(cin, expn)) {
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
	}
}

```
