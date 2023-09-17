# I/O

### include all headers
```C++
#include <bits/stdc++.h> // usefull collection of standart libraries
```

### reading line by line until eof
```C++
#include <string>

std::string line;
while(std::getline(std::cin, line)) {
   std::cout << line << "\n";
}
```

### cin & getline issues
```C++
#include <string>
#include <iostream>

std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
std::cin.clear();
std::string str;
std::getline(std::cin, str);
```

### speedup input
```C++
#include <iostream>

std::ios_base::sync_with_stdio(false); // disable sync with scanf
std::cin.tie(0); // disable syncronization with cout for speedup input
```

### `fstream + rdbuf` (to use `cin` as usual)
```C++
#include <iostream>
#include <fstream>

using namespace std;

ifstream in("input.txt");
ofstream out("output.txt");

auto cinbuf = cin.rdbuf(in.rdbuf()); //save and redirect
auto coutbuf = cout.rdbuf(out.rdbuf());

// CODE HERE...

cin.rdbuf(cinbuf);
cout.rdbuf(coutbuf);

in.close();
out.close();
```

### `freopen`
```C++
// #include <cstdio>

// freopen("input.txt", "r", stdin);
// freopen("output.txt", "w", stdout);

// // CODE HERE...

// fclose(stdin);
// fclose(stdout);
```

### `fopen`
```C++
#include <cstdio>
#pragma warning(disable : 4996)

FILE* in = fopen("input.txt", "r");
FILE* out = fopen("output.txt", "w");
int a, b;
fscanf(in, "%d %d", &a, &b);
fprintf(out, "%d %d\n", a, b);
fclose(in);
fclose(out);
```

### `fstream`
```C++
#include <fstream>

using namespace std;

fstream file;
file.open("input.txt", ios::in);

// CODE HERE...

file.close();
```