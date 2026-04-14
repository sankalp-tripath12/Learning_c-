🏆 FAANG CP COACH: C++ FROM PYTHON — COMPLETE GUIDE

MODULE 1: Basic Syntax + I/O

1. Concept Overview
C++ is a compiled, statically-typed language. Python runs line by line (interpreted). C++ converts your entire code to machine code first — that's why it's 10–100x faster than Python.
In CP, Python TLEs (Time Limit Exceeded) on problems with 10^7+ operations. C++ handles 10^8 operations per second comfortably. This is the only reason you're learning C++.

2. Python vs C++ Mapping
PYTHON                          C++
------                          ---
# comment                       // comment
print("hello")                  cout << "hello" << endl;
x = input()                     cin >> x;
x = int(input())                int x; cin >> x;
if __name__ == "__main__":      int main() { ... return 0; }
indentation = structure         { } = structure, ; ends every line
no types needed                 MUST declare type before variable

3. Syntax & Usage
The skeleton — memorize this first:
cpp#include <bits/stdc++.h>        // imports EVERYTHING (CP standard)
using namespace std;            // so you write cout not std::cout

int main() {
    // your code here
    return 0;
}
Python equivalent of the above:
python# Python has no boilerplate — but in C++ this is your "hello world" frame
I/O — the most critical skill in CP:
cpp// Reading one integer
int n;
cin >> n;

// Reading two integers on same line (like: 3 5)
int a, b;
cin >> a >> b;

// Reading a string
string s;
cin >> s;

// Printing
cout << "answer is " << n << endl;
cout << a + b << "\n";   // "\n" is faster than endl in CP — use this!

// Reading n numbers into array
int n;
cin >> n;
for (int i = 0; i < n; i++) {
    cin >> arr[i];
}
Python comparison:
pythonn = int(input())
a, b = map(int, input().split())
s = input()
print("answer is", n)

4. Key Differences from Python

Semicolons: Every statement ends with ; — forget it and nothing compiles
Curly braces: {} replaces indentation. Indentation is just style in C++, not syntax
Types are mandatory: int x = 5; not just x = 5
endl vs "\n": endl flushes the buffer (slow). Always use "\n" in CP
cin is slow by default — we fix this with Fast I/O (Module 10)
No automatic type conversion: int / int gives int — 5/2 = 2, not 2.5


5. CP Usage
Every single CP problem starts with reading input and ending with output. Getting this wrong wastes contest time. Patterns you'll see 100% of the time:
Read T test cases → loop T times → solve → print answer
Read N, then N numbers → process → print
cppint t;
cin >> t;
while (t--) {
    int n;
    cin >> n;
    // solve
    cout << answer << "\n";
}

6. Code Snippets
Template you'll use for 90% of CP problems:
cpp#include <bits/stdc++.h>
using namespace std;

int main() {
    ios_base::sync_with_stdio(false);  // Fast I/O line 1
    cin.tie(NULL);                      // Fast I/O line 2

    int t;
    cin >> t;
    while (t--) {
        int n;
        cin >> n;
        // your solution
        cout << answer << "\n";
    }
    return 0;
}
Read array of n numbers:
cppint n;
cin >> n;
vector<int> a(n);
for (int i = 0; i < n; i++) cin >> a[i];

7. Common Mistakes
MISTAKE 1: Forgetting semicolon
cout << "hello"        ← compile error

MISTAKE 2: Using endl in tight loops
cout << x << endl;     ← slow, TLE risk
cout << x << "\n";     ← correct

MISTAKE 3: Python-style print
print(x)               ← doesn't exist in C++

MISTAKE 4: No #include
cout << ...            ← works only if bits/stdc++.h included

MISTAKE 5: Integer division surprise
double ans = 5 / 2;    ← gives 2.0, not 2.5!
double ans = 5.0 / 2;  ← gives 2.5 ✓

8. Memory Tricks

cin >> x — think "scan IN to x" (arrow points INTO variable)
cout << x — think "send OUT x" (arrow points OUT from variable)
"\n" not endl — "n for ninja, ninja is fast"
bits/stdc++.h — "bits of everything" — one include rules them all
return 0 — "0 means success, main is done"


9. Practice Tasks
Task 1: Read two integers and print their sum.
Input: 3 7
Output: 10
Task 2: Read T test cases. Each has one integer N. Print N*N.
Input: 3 / 2 / 5 / 9
Output: 4 / 25 / 81
Task 3: Read a string and print it reversed.
Input: hello
Output: olleh

10. Mini Revision Sheet — Module 1
┌─────────────────────────────────────────────────┐
│  #include <bits/stdc++.h>  → import everything  │
│  using namespace std;      → drop std::          │
│  int main() { return 0; }  → entry point         │
│  cin >> x                  → read input          │
│  cout << x << "\n"         → print output        │
│  while(t--)                → T test cases        │
│  NO semicolon = NO compile                       │
│  endl is slow → always use "\n"                  │
└─────────────────────────────────────────────────┘


MODULE 2: Data Types + Variables

1. Concept Overview
Python figures out types automatically. C++ demands you declare what type a variable is before using it. This is what makes C++ fast — the compiler knows exactly how much memory to allocate.
In CP, choosing the wrong type causes overflow bugs — one of the most common sources of WA (Wrong Answer).

2. Python vs C++ Mapping
PYTHON                  C++                     SIZE / RANGE
------                  ---                     ------------
x = 5                   int x = 5;              4 bytes, ±2.1 billion
x = 5 (big number)      long long x = 5;        8 bytes, ±9.2 * 10^18
x = 3.14                double x = 3.14;        8 bytes, decimal
x = True                bool x = true;          1 byte, true/false
x = 'a'                 char x = 'a';           1 byte, single char
x = "hello"             string x = "hello";     dynamic, like Python

3. Syntax & Usage
cpp// Declaration
int a = 10;
long long b = 1000000000LL;   // LL suffix = long long literal
double c = 3.14;
bool d = true;
char e = 'z';
string f = "hello";

// Multiple declarations
int x = 1, y = 2, z = 3;

// Auto (like Python — C++ infers type) — useful but use carefully
auto g = 42;        // int
auto h = 42LL;      // long long
auto i = 3.14;      // double

// Constants (like Python's convention, but enforced)
const int MOD = 1e9 + 7;
Overflow — the silent killer in CP:
cppint a = 1e9, b = 1e9;
int c = a * b;           // OVERFLOW! int can't hold 10^18
long long c = (long long)a * b;  // CORRECT ✓
Python never overflows — it auto-promotes. C++ does NOT.

4. Key Differences from Python
Python int    → unlimited size (auto big int)
C++ int       → max ~2 * 10^9 (FIXED, overflows silently)

Python float  → actually a double internally
C++ double    → explicit, ~15 decimal digits precision

Python bool   → True/False (capital)
C++ bool      → true/false (lowercase)

Python has no char → C++ char is single character in single quotes
'a' in C++    → char
"a" in C++    → string (different!)

5. CP Usage — THE OVERFLOW GUIDE
This is the most important table in competitive programming:
Problem has numbers up to...    Use...
─────────────────────────────   ──────
10^4                            int ✓
10^9                            int ✓ (barely)
10^10 or higher                 long long ✓ (MANDATORY)
multiply two 10^5 numbers       long long ✓
mod arithmetic (1e9+7)          long long for intermediate results
counting paths/combinations     long long
coordinates in geometry         double or long long
The rule: When in doubt, use long long. Cost is minor, overflow bugs cost you AC.

6. Code Snippets
cpp// CP standard type declarations
#include <bits/stdc++.h>
using namespace std;

// These typedefs save typing in contests
typedef long long ll;
typedef pair<int,int> pii;
typedef vector<int> vi;

int main() {
    ll n;
    cin >> n;
    
    // Safe multiplication
    ll a = 1e9, b = 1e9;
    ll product = a * b;   // 10^18, fits in ll
    
    // Modular arithmetic
    const ll MOD = 1e9 + 7;
    ll result = (a % MOD * b % MOD) % MOD;
    
    cout << result << "\n";
}
Min/Max values (useful for initialization):
cppint mn = INT_MAX;      // ~2.1 billion
int mx = INT_MIN;      // ~-2.1 billion
ll mn2 = LLONG_MAX;    // ~9.2 * 10^18
ll mx2 = LLONG_MIN;
Python equivalent:
pythonmn = float('inf')
mx = float('-inf')

7. Common Mistakes
MISTAKE 1: int overflow during multiplication
int a = 100000, b = 100000;
int c = a * b;    // 10^10 > INT_MAX → garbage value, no error!

MISTAKE 2: Forgetting LL suffix
long long x = 1000000000 * 1000000000;   // RHS computed as int first!
long long x = 1000000000LL * 1000000000; // ✓

MISTAKE 3: True vs true
bool x = True;   // compile error — Python habit!
bool x = true;   // ✓

MISTAKE 4: Single vs double quotes
string s = 'hello';  // compile error
char c = "a";        // compile error
string s = "hello";  // ✓
char c = 'a';        // ✓

MISTAKE 5: Division surprise
int a = 7, b = 2;
cout << a / b;   // prints 3, not 3.5!

8. Memory Tricks

int = 4 bytes = 4 * 10^9 range → if answer > 2 billion, use ll
long long = "long long time" = stores very large numbers
ll — always typedef this on contest day
Overflow check: if you multiply two numbers and either > 10^4, think ll
true/false lowercase — C++ is case-sensitive unlike Python


9. Practice Tasks
Task 1: Read two long long numbers and print their product. Make sure no overflow.
Input: 1000000000 1000000000
Output: 1000000000000000000
Task 2: Read integer N. Print whether it's positive, negative, or zero using bool logic.
Task 3: Given A and B, compute (A * B) % (10^9 + 7).
Input: 999999999 999999999
Output: 49

10. Mini Revision Sheet — Module 2
┌──────────────────────────────────────────────────────┐
│  int        → up to ~2*10^9  (default for small)     │
│  long long  → up to ~9*10^18 (use when > 10^9)       │
│  double     → decimals                                │
│  bool       → true / false  (lowercase!)              │
│  char       → 'a'  (single quotes)                   │
│  string     → "hello" (double quotes)                 │
│                                                       │
│  typedef long long ll;  → type this every contest     │
│  Overflow rule: multiply big numbers? → cast to ll    │
│  (long long)a * b  → safe multiplication             │
│  Python True → C++ true  (critical pitfall!)          │
└──────────────────────────────────────────────────────┘


MODULE 3: Operators

1. Concept Overview
Operators in C++ are 95% identical to Python. The 5% that's different will bite you hard in contests. Focus only on the differences.

2. Python vs C++ Mapping
PYTHON              C++                 NOTES
──────              ───                 ─────
a + b               a + b               same
a - b               a - b               same
a * b               a * b               same
a / b               a / b               DIFFERENT! (int division in C++)
a // b              a / b               C++ / is Python's // for ints
a % b               a % b               same
a ** b              pow(a, b)           C++ has no ** operator!
a == b              a == b              same
a != b              a != b              same
a and b             a && b              DIFFERENT
a or b              a || b              DIFFERENT
not a               !a                  DIFFERENT
a & b               a & b               bitwise AND (same)
a | b               a | b               bitwise OR (same)
a ^ b               a ^ b               bitwise XOR (same) NOT power!
a << b              a << b              left shift (same)
a >> b              a >> b              right shift (same)

3. Syntax & Usage
cpp// Arithmetic
int a = 17, b = 5;
cout << a / b;      // 3 (integer division — truncates!)
cout << a % b;      // 2
cout << (double)a / b;  // 3.4 (cast to force float division)

// Power — no ** in C++
cout << pow(2, 10);        // 1024.0 (returns double!)
cout << (int)pow(2, 10);   // 1024

// For integer power in CP, write your own:
ll power(ll base, ll exp) {
    ll result = 1;
    while (exp--) result *= base;
    return result;
}

// Compound assignment (same as Python)
a += 5;   a -= 5;   a *= 2;   a /= 2;   a %= 3;

// Increment/Decrement (Python has no ++ or --)
a++;   // a += 1
a--;   // a -= 1
++a;   // also a += 1, but pre-increment
Bitwise operators — critical for CP:
cpp// Check if n is even/odd (faster than n % 2)
if (n & 1) cout << "odd";
else cout << "even";

// Multiply/divide by powers of 2
n << 1;   // n * 2
n >> 1;   // n / 2
n << k;   // n * 2^k

// XOR tricks (very common in CP)
a ^ a == 0;   // any number XOR itself = 0
a ^ 0 == a;   // any number XOR 0 = itself
// Find single non-duplicate in array → XOR all elements

4. Key Differences from Python
Python /   → always float division (7/2 = 3.5)
C++    /   → integer division when both operands are int (7/2 = 3)

Python **  → power operator
C++        → NO ** operator, use pow() or write your own

Python and/or/not → English keywords
C++        → &&, ||, !  (symbols only)

Python ^   → bitwise XOR
C++    ^   → also bitwise XOR (SAME — not power!)

5. CP Usage
Modular arithmetic — appears in 40% of CP problems:
cppconst int MOD = 1e9 + 7;
// (a + b) % MOD
// (a * b) % MOD
// Never: (a - b) % MOD — can be negative!
// Safe subtraction:
ll sub = ((a - b) % MOD + MOD) % MOD;
Bit tricks — fast operations:
cppn & 1           // check odd
n >> 1          // divide by 2
n << 1          // multiply by 2
__builtin_popcount(n)    // count set bits (1s in binary)
__builtin_ctz(n)         // count trailing zeros

6. Code Snippets
cpp// Safe modular multiply
ll mulmod(ll a, ll b, ll mod) {
    return (a % mod) * (b % mod) % mod;
}

// Fast power (binary exponentiation) — memorize this
ll fastpow(ll base, ll exp, ll mod) {
    ll result = 1;
    base %= mod;
    while (exp > 0) {
        if (exp & 1) result = result * base % mod;
        base = base * base % mod;
        exp >>= 1;
    }
    return result;
}

// XOR to find unique element
int findUnique(vector<int>& arr) {
    int res = 0;
    for (int x : arr) res ^= x;
    return res;
}

7. Common Mistakes
MISTAKE 1: Using ** for power
cout << 2 ** 10;    // compile error!
cout << pow(2, 10); // ✓ but returns double

MISTAKE 2: Forgetting int division
double ans = 1 / 3;    // 0.0! not 0.33
double ans = 1.0 / 3;  // 0.333 ✓

MISTAKE 3: Negative modulo
(-7) % 3 == -1 in C++ (not 2 like Python!)
Fix: ((a % MOD) + MOD) % MOD

MISTAKE 4: Using 'and', 'or', 'not'
if (a > 0 and b > 0)   // actually valid in C++ but bad style
if (a > 0 && b > 0)    // standard C++ ✓

MISTAKE 5: Overflow in pow()
int x = pow(10, 18);   // double precision loss!
Use fastpow with long long instead

8. Memory Tricks

/ in C++ = // in Python for integers — always remember this
No ** — "C++ has no stars for power, use pow()"
&& = and, || = or, ! = not — "C++ speaks symbols, not English"
^ is XOR, NOT power — same as Python, different from math notation
n & 1 — "AND 1 = last bit = odd check" — faster than %


9. Practice Tasks
Task 1: Read N and compute 2^N mod (10^9+7) using fast power.
Task 2: Read array, find the one element that appears once (all others appear twice). Use XOR.
Task 3: Read integer N. Print the number of set bits (1s in binary).
Input: 13 (binary: 1101)
Output: 3

10. Mini Revision Sheet — Module 3
┌─────────────────────────────────────────────────────┐
│  /   → integer division (C++ default for ints)      │
│  %   → modulo (can be negative for negative input!) │
│  **  → DOESN'T EXIST, use pow() or fastpow()        │
│  &&  → and    ||  → or    !  → not                 │
│  ^   → XOR (not power!)                             │
│  n & 1  → fast odd check                            │
│  n << k → n * 2^k   n >> k → n / 2^k               │
│  MOD subtraction: ((a-b)%MOD + MOD) % MOD           │
│  fastpow → binary exponentiation, memorize it       │
└─────────────────────────────────────────────────────┘


MODULE 4: Conditionals & Loops

1. Concept Overview
Logic control in C++ is syntactically different from Python but conceptually identical. The main shift: braces instead of indentation, different loop styles. C++ also has a for loop structure that Python doesn't have — and it's used in 80% of CP code.

2. Python vs C++ Mapping
PYTHON                          C++
──────                          ───
if x > 0:                       if (x > 0) {
    print("pos")                    cout << "pos\n";
elif x < 0:                     } else if (x < 0) {
    print("neg")                    cout << "neg\n";
else:                           } else {
    print("zero")                   cout << "zero\n";
                                }

for i in range(n):              for (int i = 0; i < n; i++) {
    print(i)                        cout << i << "\n";
                                }

for i in range(0, n, 2):        for (int i = 0; i < n; i += 2)
while x > 0:                    while (x > 0) {
    x -= 1                          x--;
                                }

for x in arr:                   for (int x : arr) {  ← range-based
    print(x)                        cout << x << "\n";
                                }

break / continue                break / continue  (same!)

3. Syntax & Usage
Conditionals:
cppint x = 5;

// Basic if-else
if (x > 0) {
    cout << "positive\n";
} else if (x == 0) {
    cout << "zero\n";
} else {
    cout << "negative\n";
}

// One-liner (no braces needed for single statement)
if (x > 0) cout << "positive\n";

// Ternary (very common in CP)
string result = (x > 0) ? "YES" : "NO";
cout << result << "\n";
// Python equivalent: result = "YES" if x > 0 else "NO"
Loops:
cpp// Standard for loop — most common in CP
for (int i = 0; i < n; i++) {
    cout << i << "\n";
}

// Reverse loop
for (int i = n-1; i >= 0; i--) {
    // ...
}

// Step of 2
for (int i = 0; i < n; i += 2) {
    // ...
}

// While loop
int i = 0;
while (i < n) {
    i++;
}

// Do-while (Python has no equivalent)
do {
    cin >> x;
} while (x != 0);  // runs at least once

// Range-based for (like Python's for x in arr)
vector<int> v = {1, 2, 3, 4};
for (int x : v) {
    cout << x << "\n";
}

// Range-based with reference (modifies original — Python can't do this easily)
for (int& x : v) {
    x *= 2;   // modifies the actual element
}

4. Key Differences from Python
Python: indentation defines blocks
C++:    { } defines blocks — indentation is cosmetic only

Python: elif
C++:    else if  (two words)

Python: for i in range(n)
C++:    for (int i = 0; i < n; i++)  ← 3-part loop

Python: no ternary (uses: val if cond else other)
C++:    condition ? val_if_true : val_if_false

Python: no do-while
C++:    do { } while(cond); ← runs body at least once

Python: pass (empty block placeholder)
C++:    just leave { } empty, or use ; (but avoid)

5. CP Usage
99% of CP loops are:
  - for (int i = 0; i < n; i++)          → iterate n times
  - for (int i = 1; i <= n; i++)         → 1-indexed (very common!)
  - while (t--)                           → T test cases
  - for (int x : v)                      → iterate vector
  - nested loops for 2D grids

Common CP patterns:
cpp// Pattern 1: T test cases
int t; cin >> t;
while (t--) {
    // solve one test case
}

// Pattern 2: Read n numbers, process
int n; cin >> n;
for (int i = 0; i < n; i++) {
    int x; cin >> x;
    // process x
}

// Pattern 3: Grid traversal (4 directions)
int dx[] = {0, 0, 1, -1};
int dy[] = {1, -1, 0, 0};
for (int d = 0; d < 4; d++) {
    int nx = x + dx[d];
    int ny = y + dy[d];
}

6. Code Snippets
cpp// Ternary — print YES/NO (extremely common)
cout << (condition ? "YES" : "NO") << "\n";

// Find max in array manually
int maxVal = INT_MIN;
for (int i = 0; i < n; i++) {
    if (a[i] > maxVal) maxVal = a[i];
}

// Sum of array
long long sum = 0;
for (int x : a) sum += x;

// Count elements satisfying condition
int cnt = 0;
for (int x : a) if (x % 2 == 0) cnt++;

// Nested loop (O(n^2) — brute force pattern)
for (int i = 0; i < n; i++) {
    for (int j = i+1; j < n; j++) {
        // pairs (i, j) where i < j
    }
}

7. Common Mistakes
MISTAKE 1: Missing parentheses in condition
if x > 0 { }     // compile error — Python habit!
if (x > 0) { }   // ✓

MISTAKE 2: = instead of == in condition
if (x = 5) { }   // assigns 5 to x, always true — silent bug!
if (x == 5) { }  // ✓

MISTAKE 3: Off-by-one
for (int i = 0; i <= n; i++)  // runs n+1 times!
for (int i = 0; i < n; i++)   // runs n times ✓

MISTAKE 4: elif → else if
if (a) { }
elif (b) { }   // compile error!
else if (b) {} // ✓

MISTAKE 5: Modifying vector while range-for without &
for (int x : v) x *= 2;    // modifies copy, not original!
for (int& x : v) x *= 2;   // ✓ modifies original

8. Memory Tricks

C++ for loop = 3 parts: init ; condition ; update → "ICU: I Check and Update"
while(t--) → "while tickets remain" — test cases pattern
?: ternary → think "condition ? yes-path : no-path"
else if not elif → "C++ writes it out fully"
int& x in range-for → "& means address, means real, means modify"


9. Practice Tasks
Task 1: Read N numbers. Print "EVEN" if the count of even numbers > count of odd, else "ODD".
Task 2: FizzBuzz — print 1 to N. Multiples of 3 → "Fizz", of 5 → "Buzz", of both → "FizzBuzz".
Task 3: Read a 2D grid of N×M integers. Print the row-wise maximum.

10. Mini Revision Sheet — Module 4
┌──────────────────────────────────────────────────────┐
│  if (cond) { } else if { } else { }                  │
│  for (int i = 0; i < n; i++)  → standard loop        │
│  for (int x : v)              → range-based          │
│  for (int& x : v)             → range-based + modify │
│  while (t--)                  → T test cases         │
│  cond ? a : b                 → ternary              │
│  elif → else if   (C++ is verbose here)              │
│  if (x = 5) is a BUG — use ==                        │
│  i < n not i <= n for 0-indexed loops                │
└──────────────────────────────────────────────────────┘


MODULE 5: Functions

1. Concept Overview
Functions in C++ require you to declare the return type and parameter types upfront. Python is dynamic; C++ is strict. In CP, functions help you structure solutions and write recursive algorithms cleanly.

2. Python vs C++ Mapping
PYTHON                          C++
──────                          ───
def add(a, b):                  int add(int a, int b) {
    return a + b                    return a + b;
                                }

def greet():                    void greet() {
    print("hi")                     cout << "hi\n";
                                }   // void = no return value

def solve(arr):                 void solve(vector<int>& arr) {
    pass                        }

# no return type needed         // MUST declare return type
# types auto                    // MUST declare param types

3. Syntax & Usage
cpp// Return type first, then name, then (typed params)
int multiply(int a, int b) {
    return a * b;
}

// Void — no return value
void printArr(vector<int>& v) {
    for (int x : v) cout << x << " ";
    cout << "\n";
}

// Default parameters (like Python)
int power(int base, int exp = 2) {  // exp defaults to 2
    // ...
}

// Function with multiple return values — use pair or tuple
pair<int, int> minmax(vector<int>& v) {
    int mn = *min_element(v.begin(), v.end());
    int mx = *max_element(v.begin(), v.end());
    return {mn, mx};
}

// Call it:
auto [mn, mx] = minmax(v);   // C++17 structured binding (like Python unpack)
Pass by value vs pass by reference — CRITICAL:
cpp// Pass by VALUE — function gets a copy (safe, slow for large data)
void doubleIt(int x) {
    x *= 2;   // doesn't affect original!
}

// Pass by REFERENCE — function gets the actual variable
void doubleIt(int& x) {
    x *= 2;   // DOES affect original!
}

// Pass by CONST REFERENCE — read-only, no copy (best for vectors/strings)
void printVec(const vector<int>& v) {
    for (int x : v) cout << x;
}
Python always passes objects by reference and primitives by value — in C++, you choose explicitly.

4. Key Differences from Python
Python: def name(params) — no types
C++:    returnType name(typed params) — types mandatory

Python: no explicit pass-by-reference
C++:    & makes it pass-by-reference (modifies original)

Python: multiple return → tuple
C++:    use pair<>, tuple<>, or output params

Python: functions defined anywhere, used anywhere
C++:    function must be DECLARED before it's USED
        → either define before main, or use forward declaration

Python: lambda x: x*2
C++:    [](int x) { return x * 2; }  ← lambda syntax
Forward declaration:
cpp// If you call foo() in main but define it after main:
int foo(int x);  // forward declaration at top

int main() {
    cout << foo(5);
}

int foo(int x) {
    return x * x;
}

5. CP Usage
cpp// Pattern 1: Solve function per test case (clean code)
void solve() {
    int n; cin >> n;
    // ...
    cout << ans << "\n";
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    int t; cin >> t;
    while (t--) solve();
    return 0;
}

// Pattern 2: Pass vector by reference to avoid copying
void process(vector<int>& a) {
    sort(a.begin(), a.end());
}

// Pattern 3: Lambda in sort (Module 9 preview)
sort(v.begin(), v.end(), [](int a, int b) {
    return a > b;  // descending
});

6. Code Snippets
cpp// GCD (very common in CP)
int gcd(int a, int b) {
    return b == 0 ? a : gcd(a, b);
}
// Or just use built-in:
__gcd(a, b);   // C++ built-in

// Check prime
bool isPrime(int n) {
    if (n < 2) return false;
    for (int i = 2; i * i <= n; i++)
        if (n % i == 0) return false;
    return true;
}

// Fast max of two (instead of std::max)
inline int mymax(int a, int b) { return a > b ? a : b; }
// But just use max(a, b) from STL

7. Common Mistakes
MISTAKE 1: Missing return type
add(int a, int b) { return a+b; }   // compile error
int add(int a, int b) { return a+b; } // ✓

MISTAKE 2: Forgetting & causes no modification
void increment(int x) { x++; }
int n = 5; increment(n);
cout << n;  // still 5!

MISTAKE 3: Passing large vector by value
void process(vector<int> v) { }  // copies entire vector — slow!
void process(vector<int>& v) { } // passes reference — fast ✓

MISTAKE 4: Using function before declaring it
int main() { foo(); }
int foo() { }  // error: foo not declared before use
// Fix: define foo before main, or add forward declaration

MISTAKE 5: Wrong return type
int f() { return 3.7; }  // truncates to 3, no error — silent bug!

8. Memory Tricks

void = "void of return value" = Python's no-return function
& in param = "address = real = modifies original"
const & = "read-only reference" = fast + safe for large inputs
C++ needs type before everything: return type, param type — "everything has a label"
solve() + while(t--) solve() = the CP contest structure, always


9. Practice Tasks
Task 1: Write function bool isPalindrome(string s) and test it.
Task 2: Write function that takes a vector by reference and replaces all negatives with 0.
Task 3: Write a solve() function that reads N, reads N numbers, and prints their average (as double).

10. Mini Revision Sheet — Module 5
┌──────────────────────────────────────────────────────────┐
│  returnType funcName(type param) { return val; }         │
│  void → no return                                        │
│  & in param → pass by reference, modifies original       │
│  const& → fast read-only (use for vector/string params)  │
│  Define before use OR use forward declaration            │
│  pair<int,int> → return two values                       │
│  auto [a, b] = func() → unpack pair (C++17)             │
│  while(t--) solve(); → contest structure                 │
│  __gcd(a, b) → built-in GCD, memorize it                │
└──────────────────────────────────────────────────────────┘


MODULE 6: Arrays & Strings

1. Concept Overview
C++ arrays are fixed-size, no bounds checking, no auto-resize. They're fast because they're raw memory. Strings are mutable (unlike Python). In CP, raw arrays are used for speed; vectors (Module 7) are used for flexibility. Know both.

2. Python vs C++ Mapping
PYTHON                          C++
──────                          ───
arr = [0] * n                   int arr[n];          ← stack array
arr = [1, 2, 3]                 int arr[] = {1,2,3};
len(arr)                        sizeof(arr)/sizeof(arr[0])  ← ugly
arr[0]                          arr[0]               same indexing
arr[-1]                         arr[n-1]             NO negative indexing!
s = "hello"                     string s = "hello";
s[0]                            s[0]                 same
s + " world"                    s + " world"         same (concatenation)
len(s)                          s.length() or s.size()
s[1:4]                          s.substr(1, 3)       (start, LENGTH not end!)
str(42)                         to_string(42)
int("42")                       stoi("42")
s.split()                       (manual — no split() in C++)

3. Syntax & Usage
Arrays:
cpp// Fixed array — size must be known at compile time (or use constant)
int arr[5] = {1, 2, 3, 4, 5};
int arr[5] = {};         // all zeros
int arr[5];              // uninitialized — garbage values! (Python initializes to 0)

// Global arrays (initialized to 0 automatically — prefer in CP for large arrays)
int dp[100005];          // global → safe, all zeros

// 2D array
int grid[100][100] = {};  // 100x100 grid, all zeros
grid[i][j] = 5;

// Array size
int n = sizeof(arr) / sizeof(arr[0]);

// Iterate
for (int i = 0; i < 5; i++) cout << arr[i] << " ";
Strings:
cppstring s = "hello";

// Access characters
cout << s[0];        // 'h'
cout << s.back();    // 'o' (last char — Python's s[-1])
cout << s.front();   // 'h' (first char)

// Length
cout << s.length();  // 5

// Substring — NOTE: (start, LENGTH) not (start, end)!
cout << s.substr(1, 3);  // "ell"  (start=1, length=3)
// Python: s[1:4]

// Find
int pos = s.find("ll");  // returns 2; returns string::npos if not found
if (s.find("ll") != string::npos) cout << "found";

// Append
s += " world";     // s = "hello world"
s.push_back('!'); // append char

// Erase
s.erase(0, 5);    // removes 5 chars starting at index 0

// Convert int ↔ string
string x = to_string(42);    // "42"
int n = stoi("123");         // 123
long long ll = stoll("123"); // for long long

// Iterate over characters
for (char c : s) cout << c;
for (int i = 0; i < s.size(); i++) cout << s[i];

// Check character type
isdigit('5')   // true
isalpha('a')   // true
islower('a')   // true
isupper('A')   // true
tolower('A')   // 'a'
toupper('a')   // 'A'

4. Key Differences from Python
Python arr[-1]         → C++ arr[n-1]     (no negative indexing!)
Python s[1:4]          → C++ s.substr(1, 3)  (2nd arg is LENGTH, not end!)
Python len(s)          → C++ s.size() or s.length()
Python str(n)          → C++ to_string(n)
Python int(s)          → C++ stoi(s)
Python s.split()       → C++ manual parsing with cin or stringstream
Python arr grows       → C++ raw array is FIXED size (use vector for growth)
Python arr initialized → C++ local array has GARBAGE values (init manually!)

5. CP Usage
cpp// Global array for DP (large, auto-zero initialized)
int dp[100005];
int vis[100005];   // visited array for BFS/DFS

// Character frequency count (very common)
int freq[26] = {};  // a=0, b=1, ..., z=25
for (char c : s) freq[c - 'a']++;

// String to char array (for manipulation)
for (int i = 0; i < s.size(); i++) {
    if (s[i] == 'a') s[i] = 'b';
}

// Palindrome check
bool isPalin(string& s) {
    int l = 0, r = s.size() - 1;
    while (l < r) {
        if (s[l] != s[r]) return false;
        l++; r--;
    }
    return true;
}

// Read line with spaces (cin stops at space!)
string line;
getline(cin, line);   // like Python's input()

6. Code Snippets
cpp// Frequency array — character counting
string s; cin >> s;
int freq[26] = {};
for (char c : s) freq[c - 'a']++;
for (int i = 0; i < 26; i++)
    if (freq[i]) cout << (char)('a'+i) << ": " << freq[i] << "\n";

// Reverse a string
reverse(s.begin(), s.end());  // in-place

// Sort a string
sort(s.begin(), s.end());

// Check if two strings are anagrams
bool isAnagram(string a, string b) {
    sort(a.begin(), a.end());
    sort(b.begin(), b.end());
    return a == b;
}

// Split string by spaces using stringstream
stringstream ss(input);
string token;
vector<string> words;
while (ss >> token) words.push_back(token);

7. Common Mistakes
MISTAKE 1: substr second arg is LENGTH, not end index
s.substr(1, 4)   // chars at index 1,2,3,4 — length 4
// Python: s[1:5] — same result but different argument meaning!

MISTAKE 2: Uninitialized local array
int arr[100];
cout << arr[0];   // garbage value! not 0!
int arr[100] = {}; // ✓ all zeros

MISTAKE 3: Negative indexing
s[-1]    // undefined behavior — Python habit!
s[s.size()-1] or s.back()  // ✓

MISTAKE 4: cin doesn't read full line
cin >> s;          // stops at space!
getline(cin, s);   // reads whole line ✓

MISTAKE 5: Comparing size() with negative int
if (s.size() - 1 >= 0)  // ALWAYS true! size() is unsigned
if ((int)s.size() - 1 >= 0)  // ✓ cast to int first

8. Memory Tricks

substr(start, LENGTH) — "length, not end" — tattoo this
s.back() = last element, s.front() = first — like a deque
freq[c - 'a'] — "c minus a gives index 0-25" — frequency trick
string::npos — "not a position" — returned when find fails
Global arrays = auto-zero — declare big arrays globally in CP always
to_string() / stoi() — conversion pair, memorize together


9. Practice Tasks
Task 1: Read string S. Print frequency of each character that appears.
Task 2: Read string S. Check if it's a palindrome without using reverse().
Task 3: Read two strings. Check if they're anagrams.

10. Mini Revision Sheet — Module 6
┌──────────────────────────────────────────────────────────┐
│  int arr[n] = {};         → array, all zeros             │
│  s.substr(start, length)  → NOT (start, end)!           │
│  s.size() / s.length()    → string length               │
│  s.back()                 → last char (Python s[-1])     │
│  to_string(n)             → int to string                │
│  stoi(s)                  → string to int                │
│  freq[c - 'a']++          → character frequency pattern  │
│  getline(cin, s)          → read full line               │
│  No negative indexing     → use s[n-1] or s.back()      │
│  Local array → garbage    → always initialize!           │
└──────────────────────────────────────────────────────────┘


MODULE 7: Vectors (VERY IMPORTANT)

1. Concept Overview
Vector = Python list. This is the most important C++ data structure for CP. It's a dynamic array that resizes automatically. 70% of your C++ code will use vectors. Master this completely.

2. Python vs C++ Mapping
PYTHON                          C++
──────                          ───
arr = []                        vector<int> v;
arr = [0] * n                   vector<int> v(n, 0);
arr = [1, 2, 3]                 vector<int> v = {1, 2, 3};
arr.append(x)                   v.push_back(x);
arr.pop()                       v.pop_back();
len(arr)                        v.size()
arr[0]                          v[0]
arr[-1]                         v.back()
arr[0] = 5                      v[0] = 5
arr.sort()                      sort(v.begin(), v.end())
arr[::-1]                       reverse(v.begin(), v.end())
x in arr                        find(v.begin(),v.end(),x)!=v.end()
arr.clear()                     v.clear()
arr2 = arr[:]                   vector<int> v2 = v; (copy)
2D: [[0]*m for _ in range(n)]   vector<vector<int>> g(n, vector<int>(m, 0));

3. Syntax & Usage
cpp#include <bits/stdc++.h>
using namespace std;

// Declaration
vector<int> v;                    // empty
vector<int> v(5);                 // [0,0,0,0,0]
vector<int> v(5, -1);            // [-1,-1,-1,-1,-1]
vector<int> v = {1, 2, 3, 4};   // initialized

// Add/Remove
v.push_back(10);   // append to end
v.pop_back();      // remove from end
v.insert(v.begin() + 2, 99);  // insert 99 at index 2 (slow O(n))
v.erase(v.begin() + 1);       // remove at index 1 (slow O(n))

// Access
v[0];         // first element
v.back();     // last element  (Python: v[-1])
v.front();    // first element (Python: v[0])

// Size
v.size();     // number of elements (returns unsigned int!)
v.empty();    // true if size == 0

// Iterate
for (int i = 0; i < v.size(); i++) cout << v[i];
for (int x : v) cout << x;        // range-based (preferred)
for (int& x : v) x *= 2;          // modify while iterating

// Sort
sort(v.begin(), v.end());           // ascending
sort(v.rbegin(), v.rend());         // descending (r = reverse)

// Reverse
reverse(v.begin(), v.end());

// Fill with value
fill(v.begin(), v.end(), 0);

// Resize
v.resize(10);       // resize to 10 elements
v.resize(10, -1);   // resize to 10, new elements = -1

// Clear
v.clear();   // empties the vector

// 2D Vector
int n = 3, m = 4;
vector<vector<int>> grid(n, vector<int>(m, 0));
grid[1][2] = 5;

4. Key Differences from Python
Python list.append()   → C++ v.push_back()    (name different)
Python list.pop()      → C++ v.pop_back()      (back only, no index)
Python len(v)          → C++ v.size()          (method, not function)
Python v[-1]           → C++ v.back()          (no negative index)
Python sorted(v)       → C++ sort(v.begin(), v.end()) returns nothing, in-place
Python v[1:3]          → C++ no slice! use loops or copy constructor
Python x in v          → C++ find() or binary search
Python list is 0-overhead → C++ v.size() is unsigned — compare with (int)v.size()

5. CP Usage
cpp// Pattern 1: Read n numbers into vector
int n; cin >> n;
vector<int> a(n);
for (int i = 0; i < n; i++) cin >> a[i];

// Pattern 2: Adjacency list for graphs
int n, m; cin >> n >> m;
vector<vector<int>> adj(n + 1);
for (int i = 0; i < m; i++) {
    int u, v; cin >> u >> v;
    adj[u].push_back(v);
    adj[v].push_back(u);
}

// Pattern 3: Prefix sum
vector<int> pre(n + 1, 0);
for (int i = 0; i < n; i++) pre[i+1] = pre[i] + a[i];
// Query sum [l, r]: pre[r+1] - pre[l]

// Pattern 4: Sorting with index tracking
vector<pair<int,int>> v(n);
for (int i = 0; i < n; i++) v[i] = {a[i], i};
sort(v.begin(), v.end());  // sorts by first element (value)

6. Code Snippets
cpp// Read vector
vector<int> readVec(int n) {
    vector<int> v(n);
    for (int& x : v) cin >> x;
    return v;
}

// Print vector
void printVec(vector<int>& v) {
    for (int x : v) cout << x << " ";
    cout << "\n";
}

// Prefix sum setup
vector<long long> prefixSum(vector<int>& a) {
    int n = a.size();
    vector<long long> pre(n + 1, 0);
    for (int i = 0; i < n; i++) pre[i+1] = pre[i] + a[i];
    return pre;
}

// Frequency vector
vector<int> freq(26, 0);
for (char c : s) freq[c - 'a']++;

7. Common Mistakes
MISTAKE 1: Comparing int and unsigned size()
for (int i = 0; i < v.size() - 1; i++)
// If v is empty, v.size()-1 underflows (unsigned!) → huge number → infinite loop
// Fix:
for (int i = 0; i + 1 < (int)v.size(); i++)

MISTAKE 2: push_back vs append
v.append(5);       // doesn't exist!
v.push_back(5);    // ✓

MISTAKE 3: pop returns nothing
int x = v.pop_back();  // doesn't return!
int x = v.back(); v.pop_back();  // ✓ save then remove

MISTAKE 4: Slicing doesn't work
auto sub = v[1:3];   // compile error!
vector<int> sub(v.begin()+1, v.begin()+3); // ✓

MISTAKE 5: Accessing after pop
v.pop_back();
cout << v.back();  // if v was size 1, this is UB (undefined behavior)

8. Memory Tricks

push_back = "push to back" = Python append
v.begin(), v.end() = "point to start and one-past-end" — every STL algo needs these
sort(v.begin(), v.end()) — memorize this as one unit
v.back() = Python's v[-1]
vector<vector<int>> g(n, vector<int>(m, 0)) = 2D grid — read it as "n rows, each row is a vector of m zeros"
(int)v.size() — always cast to int when comparing to avoid unsigned bugs


9. Practice Tasks
Task 1: Read N numbers, sort them, print the median.
Task 2: Read N numbers. Answer Q queries: each query gives L R, print sum of elements from index L to R (use prefix sum).
Task 3: Build adjacency list for undirected graph with N nodes and M edges. Print neighbor list for each node.

10. Mini Revision Sheet — Module 7
┌──────────────────────────────────────────────────────────┐
│  vector<int> v(n, 0)          → n zeros                 │
│  v.push_back(x)               → append                  │
│  v.pop_back()                 → remove last             │
│  v.back()                     → last element            │
│  v.size()                     → length (cast to int!)   │
│  sort(v.begin(), v.end())     → sort ascending          │
│  sort(v.rbegin(), v.rend())   → sort descending         │
│  reverse(v.begin(), v.end())  → reverse in-place        │
│  vector<vector<int>> g(n, vector<int>(m,0)) → 2D grid  │
│  Always (int)v.size() when comparing with int           │
└──────────────────────────────────────────────────────────┘


MODULE 8: STL Basics (set, map, pair)

1. Concept Overview
STL = Standard Template Library. These are pre-built data structures in C++ that correspond to Python's set, dict, and tuple. They're optimized and critical for CP. Master pair, set, and map — they appear in nearly every medium+ problem.

2. Python vs C++ Mapping
PYTHON                          C++
──────                          ───
tuple (a, b)                    pair<int, int> p = {a, b};
s = set()                       set<int> s;
s.add(x)                        s.insert(x);
s.remove(x)                     s.erase(x);
x in s                          s.count(x) or s.find(x)!=s.end()
d = dict()                      map<int, int> d;
d[key] = val                    d[key] = val;
d.get(key, 0)                   d.count(key) ? d[key] : 0
key in d                        d.count(key) > 0
for k, v in d.items()           for (auto& [k, v] : d)
sorted(s)                       set is ALWAYS sorted in C++!
Counter(arr)                    map<int,int> freq; for(x:arr) freq[x]++;

3. Syntax & Usage
PAIR — the building block:
cpppair<int, int> p = {3, 5};
pair<int, string> p2 = {1, "hello"};

p.first;    // 3
p.second;   // 5

// Make pair
auto p3 = make_pair(10, 20);

// Pairs sort by first, then second — very useful!
vector<pair<int,int>> v = {{3,1},{1,2},{3,0}};
sort(v.begin(), v.end());
// Result: {{1,2},{3,0},{3,1}}
SET — sorted, unique elements:
cppset<int> s;
s.insert(3);
s.insert(1);
s.insert(4);
s.insert(1);   // ignored! already exists

// s is now: {1, 3, 4}  ← always sorted!

s.erase(3);
s.count(1);    // 1 if exists, 0 if not — use for membership check
s.size();
s.empty();

// Iterate — always in sorted order
for (int x : s) cout << x << " ";

// Find
auto it = s.find(3);
if (it != s.end()) cout << "found";

// Lower/upper bound
auto it = s.lower_bound(3);  // iterator to first element >= 3
auto it = s.upper_bound(3);  // iterator to first element > 3
MAP — key-value store:
cppmap<string, int> freq;

freq["apple"] = 5;
freq["banana"] = 3;
freq["apple"]++;   // increment

// Access (creates key with 0 if not exists!)
cout << freq["apple"];

// Safe access
if (freq.count("apple")) cout << freq["apple"];

// Iterate — sorted by key!
for (auto& [key, val] : freq) {   // C++17 structured binding
    cout << key << ": " << val << "\n";
}
// Or without structured binding:
for (auto& p : freq) {
    cout << p.first << ": " << p.second << "\n";
}

// Erase
freq.erase("banana");

// Size
freq.size();

4. Key Differences from Python
Python set    → unordered
C++ set       → ALWAYS SORTED (uses BST internally)
C++ unordered_set → like Python set (hash-based, faster but no order)

Python dict   → unordered (Python 3.7+ insertion-ordered)
C++ map       → ALWAYS SORTED by key (BST)
C++ unordered_map → like Python dict (hash-based, faster)

Python dict[key] → KeyError if missing
C++ map[key]    → creates key with default 0! No error

C++ set/map operations → O(log n)
C++ unordered_set/map  → O(1) average

Prefer unordered_map/unordered_set for pure speed in CP
Use map/set when you need sorted order or lower_bound

5. CP Usage
cpp// Frequency counting (like Counter in Python)
map<int, int> freq;
for (int x : arr) freq[x]++;

// Or faster:
unordered_map<int, int> freq;
for (int x : arr) freq[x]++;

// Check duplicates
set<int> seen;
for (int x : arr) {
    if (seen.count(x)) { cout << "duplicate!"; break; }
    seen.insert(x);
}

// Nearest smaller/larger element (using lower_bound)
set<int> s;
s.insert(x);
auto it = s.lower_bound(x);  // first element >= x
if (it != s.begin()) { --it; /* largest element < x */ }
Pairs for sorting with metadata:
cpp// Sort by value descending, keeping original index
vector<pair<int,int>> v(n);
for (int i = 0; i < n; i++) v[i] = {-a[i], i};  // negate for descending
sort(v.begin(), v.end());
// Now v[0].second is index of max element

6. Code Snippets
cpp// Word frequency counter
map<string, int> wordCount(vector<string>& words) {
    map<string, int> freq;
    for (string& w : words) freq[w]++;
    return freq;
}

// Find mode (most frequent element)
int findMode(vector<int>& arr) {
    unordered_map<int,int> freq;
    for (int x : arr) freq[x]++;
    int mode = arr[0], maxFreq = 0;
    for (auto& [val, cnt] : freq)
        if (cnt > maxFreq) { maxFreq = cnt; mode = val; }
    return mode;
}

// Two sum using map
pair<int,int> twoSum(vector<int>& a, int target) {
    unordered_map<int,int> seen;
    for (int i = 0; i < a.size(); i++) {
        int need = target - a[i];
        if (seen.count(need)) return {seen[need], i};
        seen[a[i]] = i;
    }
    return {-1, -1};
}

7. Common Mistakes
MISTAKE 1: map[] creates a key
if (m["key"] == 0)  // creates "key" with value 0 even if checking!
if (m.count("key") && m["key"] == 0)  // ✓

MISTAKE 2: Assuming set is unordered
set<int> s = {3, 1, 4, 1, 5};
// s is {1, 3, 4, 5} — sorted, not insertion order!

MISTAKE 3: Modifying set while iterating
for (int x : s) s.erase(x);   // undefined behavior!

MISTAKE 4: pair access
p[0]      // doesn't work!
p.first   // ✓

MISTAKE 5: Using map when unordered_map is faster
// If you don't need sorted order, unordered_map is O(1) vs O(log n)
// In tight loops, this matters for TLE

8. Memory Tricks

pair = tuple of 2 → .first and .second (not index!)
set = sorted, unique Python set — "sorted set"
map = sorted Python dict — "sorted map"
count(x) = "1 if exists, 0 if not" — use for membership (not find)
lower_bound = "lower boundary = first ≥ x"
unordered_ prefix = "hash = faster but no order"
map[key]++ pattern = frequency counter — write this from muscle memory


9. Practice Tasks
Task 1: Read N numbers. Print the number of distinct values.
Task 2: Read a sentence (multiple words). Print each word and its frequency, sorted by word.
Task 3: Two Sum — read array and target, print indices of two numbers that sum to target.

10. Mini Revision Sheet — Module 8
┌──────────────────────────────────────────────────────────┐
│  pair<int,int> p = {a,b}; p.first; p.second             │
│  set<int> s → sorted unique, O(log n)                   │
│  s.insert(x); s.erase(x); s.count(x);                   │
│  s.lower_bound(x) → first ≥ x                           │
│  map<k,v> m → sorted by key, O(log n)                   │
│  m[key]++  → frequency counter                          │
│  m.count(key) → safe membership check (not m[key]!)     │
│  unordered_map/set → O(1) avg, use when order not needed │
│  for(auto&[k,v]:m) → iterate map (C++17)               │
│  pair sorts by first then second — use for custom sort   │
└──────────────────────────────────────────────────────────┘


MODULE 9: Sorting + Custom Comparator

1. Concept Overview
Sorting is in 50%+ of CP problems. C++ sort is O(n log n) introsort — extremely fast. The killer feature: custom comparators let you sort by any logic, which Python does too but C++ syntax is different.

2. Python vs C++ Mapping
PYTHON                              C++
──────                              ───
arr.sort()                          sort(v.begin(), v.end());
sorted(arr)                         sort() is in-place, no return value
arr.sort(reverse=True)              sort(v.rbegin(), v.rend());
arr.sort(key=lambda x: x[1])        sort(v.begin(),v.end(),[](auto& a,auto& b){
                                        return a[1] < b[1]; });
arr.sort(key=lambda x: -x)          sort(v.begin(),v.end(),greater<int>());

3. Syntax & Usage
cppvector<int> v = {5, 2, 8, 1, 9};

// Ascending (default)
sort(v.begin(), v.end());
// v = {1, 2, 5, 8, 9}

// Descending
sort(v.begin(), v.end(), greater<int>());
// or:
sort(v.rbegin(), v.rend());

// Sort partial range [begin+l, begin+r)
sort(v.begin() + 1, v.begin() + 4);  // sort index 1,2,3 only

// Custom comparator with lambda
sort(v.begin(), v.end(), [](int a, int b) {
    return a > b;   // return true means a should come BEFORE b
});

// Sort vector of pairs by second element
vector<pair<int,int>> p = {{1,5},{3,2},{2,8}};
sort(p.begin(), p.end(), [](auto& a, auto& b) {
    return a.second < b.second;
});
// Sorted by second: {3,2},{1,5},{2,8}

// Sort by multiple criteria
sort(p.begin(), p.end(), [](auto& a, auto& b) {
    if (a.first != b.first) return a.first < b.first;  // primary: first asc
    return a.second > b.second;  // secondary: second desc
});
Custom comparator for structs:
cppstruct Student {
    string name;
    int grade;
};

vector<Student> students = {{"Alice",90},{"Bob",85},{"Carol",90}};

// Sort by grade desc, then name asc
sort(students.begin(), students.end(), [](const Student& a, const Student& b) {
    if (a.grade != b.grade) return a.grade > b.grade;
    return a.name < b.name;
});

4. Key Differences from Python
Python: sorted() returns new list, .sort() in-place
C++:    sort() is ALWAYS in-place, returns nothing

Python: key=lambda x: x[1]  (transforms element to sort key)
C++:    comparator (a, b) → returns true if a comes before b
        DIFFERENT mental model!

Python: arr.sort(key=lambda x: -x)  (negate for reverse)
C++:    sort(v.rbegin(), v.rend()) or greater<int>()

Python: stable_sort not default
C++:    stable_sort(v.begin(), v.end())  exists and is stable
        sort() is NOT guaranteed stable (use stable_sort if order matters)

5. CP Usage
cpp// Greedy: sort by deadline
sort(jobs.begin(), jobs.end(), [](auto& a, auto& b) {
    return a.deadline < b.deadline;
});

// Sort indices by value (without modifying original array)
vector<int> idx(n);
iota(idx.begin(), idx.end(), 0);  // idx = {0,1,2,...,n-1}
sort(idx.begin(), idx.end(), [&](int i, int j) {
    return a[i] < a[j];  // sort indices by a's values
});

// Coordinate compression
vector<int> sorted_v = v;
sort(sorted_v.begin(), sorted_v.end());
sorted_v.erase(unique(sorted_v.begin(), sorted_v.end()), sorted_v.end());
// Now sorted_v[i] = i-th distinct value
// Find rank: lower_bound(sorted_v.begin(), sorted_v.end(), x) - sorted_v.begin()

6. Code Snippets
cpp// Sort descending — two ways
sort(v.rbegin(), v.rend());
sort(v.begin(), v.end(), greater<int>());

// Sort by absolute value
sort(v.begin(), v.end(), [](int a, int b) {
    return abs(a) < abs(b);
});

// Coordinate compression template
auto compress = [](vector<int> v) {
    vector<int> s = v;
    sort(s.begin(), s.end());
    s.erase(unique(s.begin(), s.end()), s.end());
    for (int& x : v)
        x = lower_bound(s.begin(), s.end(), x) - s.begin();
    return v;
};

// nth_element — O(n) partial sort (find kth smallest)
nth_element(v.begin(), v.begin() + k, v.end());
cout << v[k];  // kth smallest element

7. Common Mistakes
MISTAKE 1: Comparator returns true when equal
sort(v.begin(), v.end(), [](int a, int b) {
    return a <= b;  // BUG! must be strict less than
});
// If a == b returns true, undefined behavior (strict weak ordering violation)
// Always use < not <=

MISTAKE 2: Capturing by value when lambda needs array
sort(idx.begin(), idx.end(), [](int i, int j) {
    return a[i] < a[j];  // a not visible!
});
// Fix: capture by reference
sort(idx.begin(), idx.end(), [&](int i, int j) {
    return a[i] < a[j];  // ✓ [&] captures all variables by reference
});

MISTAKE 3: Assuming sort is stable
// Equal elements may be reordered — use stable_sort if original order matters

MISTAKE 4: Sorting wrong range
sort(v.begin(), v.end() + 1);  // out of bounds! undefined behavior

8. Memory Tricks

sort(v.begin(), v.end()) — "begin to end, always"
Comparator returns true = "a goes first" — "return true = a wins"
[&] in lambda — "& = borrow everything from outside"
greater<int>() — "greater means descending" — counter-intuitive but memorize it
rbegin(), rend() — "r = reverse" for descending sort
Strict < in comparator — NEVER use <= — "strict or crash"


9. Practice Tasks
Task 1: Sort array of strings by length, then alphabetically for ties.
Task 2: Given N students with name and marks, sort by marks descending, then by name ascending for ties.
Task 3: Implement coordinate compression: given array with values up to 10^9, compress to range [0, k).

10. Mini Revision Sheet — Module 9
┌──────────────────────────────────────────────────────────┐
│  sort(v.begin(), v.end())          → ascending           │
│  sort(v.rbegin(), v.rend())        → descending          │
│  sort(..., greater<int>())         → descending          │
│  Lambda: [](int a, int b){ return a < b; }               │
│  Return true = a comes FIRST                             │
│  NEVER use <= in comparator (strict weak ordering!)      │
│  [&] in lambda to access outer variables                 │
│  stable_sort → preserves equal element order            │
│  iota + sort-indices pattern for index-based sort        │
│  unique() + erase() → remove duplicates from sorted vec  │
└──────────────────────────────────────────────────────────┘


MODULE 10: Fast I/O + Macros

1. Concept Overview
In CP, I/O can be the bottleneck. If a problem has 10^6 inputs, slow I/O causes TLE even if your algorithm is perfect. Fast I/O is a 2-line fix. Macros save typing in contests — they're shortcuts that the compiler replaces before compiling.

2. Python vs C++ Mapping
PYTHON                          C++  (before fast I/O)
──────                          ───
input() = fast enough           cin >> x  (sync with C stdio = slow!)

After fast I/O:
sys.stdin.readline()    ≈       cin >> x  (after sync_with_stdio(false))

3. Syntax & Usage
Fast I/O — add these 2 lines at start of main():
cppint main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    // ... rest of code
}
What do these do?

sync_with_stdio(false) → decouples cin/cout from C's scanf/printf (much faster)
cin.tie(NULL) → stops cin from flushing cout before each read

WARNING: After these lines, do NOT mix scanf/printf with cin/cout. Pick one.
Macros — your contest shortcuts:
cpp// Common CP macro set — put these after #include at top
#define int long long          // makes ALL ints long long (overflow-safe!)
#define pb push_back
#define ff first
#define ss second
#define all(v) v.begin(), v.end()
#define sz(v) (int)v.size()
#define vi vector<int>
#define pii pair<int,int>
#define MOD 1000000007

// With these macros:
v.push_back(x)        → v.pb(x)
sort(v.begin(),v.end())  → sort(all(v))
p.first               → p.ff
p.second              → p.ss
Full CP Template:
cpp#include <bits/stdc++.h>
using namespace std;

#define int long long
#define pb push_back
#define all(v) v.begin(), v.end()
#define sz(v) (int)v.size()
#define MOD 1000000007LL

void solve() {
    // your solution here
}

signed main() {       // NOTE: signed main, not int main, when #define int long long
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    int t = 1;
    cin >> t;
    while (t--) solve();
    
    return 0;
}

4. Key Differences from Python
Python: I/O is already reasonably fast for CP scale
C++:    cin/cout sync is slow by default — MUST disable for heavy I/O

Python: no macros
C++:    #define = text replacement before compile (not a function!)

Python: print() adds newline by default
C++:    cout doesn't — you must add "\n" or endl (use "\n"!)

Python: print(*arr) → space-separated
C++:    for (int x : v) cout << x << " "; cout << "\n";

5. CP Usage
cpp// Reading n pairs
int n; cin >> n;
vector<pair<int,int>> edges(n);
for (auto& [u, v] : edges) cin >> u >> v;

// Print space-separated
for (int i = 0; i < n; i++) {
    cout << a[i];
    if (i < n-1) cout << " ";
}
cout << "\n";

// Or simpler:
for (int x : v) cout << x << " ";
cout << "\n";

// Reading until EOF (when n not given)
int x;
while (cin >> x) {
    // process x
}

6. Code Snippets
cpp// Master CP template — use this every contest
#include <bits/stdc++.h>
using namespace std;

typedef long long ll;
typedef pair<int,int> pii;
typedef vector<int> vi;
typedef vector<ll> vll;

#define pb push_back
#define all(v) v.begin(), v.end()
#define sz(v) (int)(v).size()
#define F first
#define S second
#define MOD 1000000007LL

void solve() {
    int n;
    cin >> n;
    vi a(n);
    for (int& x : a) cin >> x;
    
    // solution
    
    cout << ans << "\n";
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    int t = 1;
    // cin >> t;   // uncomment for multi-test
    while (t--) solve();
    return 0;
}

7. Common Mistakes
MISTAKE 1: Forgetting fast I/O on large input
10^6 integers with slow cin → TLE

MISTAKE 2: Mixing scanf with fast cin
ios_base::sync_with_stdio(false);
scanf("%d", &x);  // undefined behavior! use cin only after sync=false

MISTAKE 3: #define int long long but int main()
#define int long long
int main() { }   // main becomes "long long main" — compile error on some compilers
signed main() { } // ✓ always use signed main with this macro

MISTAKE 4: endl with heavy output
for (int i = 0; i < 1e6; i++) cout << i << endl;  // flushes 10^6 times! TLE
for (int i = 0; i < 1e6; i++) cout << i << "\n";  // ✓

MISTAKE 5: Macro with side effects
#define sq(x) x*x
sq(2+3) expands to 2+3*2+3 = 11, not 25!
// Use functions or: #define sq(x) ((x)*(x))

8. Memory Tricks

ios_base::sync_with_stdio(false); cin.tie(NULL); — memorize as a single block, paste always
"\n" not endl — "n is narrow and fast, endl is fat and slow"
#define int long long — "one macro eliminates all overflow anxiety"
signed main() — "signed when int is redefined"
all(v) macro = "all of vector = begin to end" — saves 20+ chars per sort


9. Practice Tasks
Task 1: Write the full CP template from memory (without looking). Time yourself — should be under 60 seconds.
Task 2: Read 10^6 integers and print their sum. Verify fast I/O is working (should run < 0.5s).
Task 3: Read N, then N space-separated numbers on one line, and print them in reverse on one line.

10. Mini Revision Sheet — Module 10
┌──────────────────────────────────────────────────────────┐
│  ios_base::sync_with_stdio(false);  ← ALWAYS             │
│  cin.tie(NULL);                     ← ALWAYS             │
│  "\n" not endl                      ← ALWAYS             │
│  #define int long long → signed main()                   │
│  #define all(v) v.begin(), v.end()                       │
│  #define pb push_back                                    │
│  #define MOD 1000000007LL                                │
│  Don't mix scanf/printf after sync_with_stdio(false)     │
│  Template: #include → macros → solve() → main() → done  │
└──────────────────────────────────────────────────────────┘


MODULE 11: Pointers (CP-Relevant Only)

1. Concept Overview
Python hides pointers completely. In CP, you need pointers mainly for: linked lists, trees, dynamic memory, and understanding references. We'll skip low-level pointer arithmetic and focus only on what CP needs.

2. Python vs C++ Mapping
PYTHON                          C++
──────                          ───
x = 5                           int x = 5;
# no pointer concept            int* p = &x;   (p points to x)
# everything is a reference     *p = 10;       (change x via p)
id(x)                           &x   (memory address of x)
obj.attr                        ptr->attr  (access via pointer)
None                            nullptr  (null pointer)

3. Syntax & Usage
cppint x = 10;
int* p = &x;    // p stores ADDRESS of x

cout << x;      // 10  (value)
cout << &x;     // 0x... (address of x)
cout << p;      // 0x... (same address, that's what p holds)
cout << *p;     // 10   (* = dereference = go to address and get value)

*p = 99;        // changes x through pointer
cout << x;      // 99

// Null pointer
int* ptr = nullptr;   // like Python's None
if (ptr == nullptr) cout << "null";

// Pointer to struct/class (used in trees, linked lists)
struct Node {
    int val;
    Node* left;
    Node* right;
    Node(int v) : val(v), left(nullptr), right(nullptr) {}
};

Node* root = new Node(5);   // dynamic allocation (heap)
root->left = new Node(3);   // -> = access member via pointer
root->right = new Node(7);

// Delete when done (but in CP, we often just let it leak)
delete root;
References vs Pointers:
cppint x = 5;
int& ref = x;   // reference — like an alias, always valid
ref = 10;       // x is now 10

int* ptr = &x;  // pointer — can be null, can change what it points to
*ptr = 20;      // x is now 20

// In CP, prefer references (&) over pointers where possible
// Pointers mainly needed for tree/graph node structures

4. Key Differences from Python
Python: every variable is a reference internally
C++:    variables are values by default; & makes a reference; * makes a pointer

Python: no manual memory management
C++:    new = allocate on heap, delete = free (in CP we often skip delete)

Python: obj.attr  always
C++:    object.attr  for actual object
        pointer->attr  for pointer to object
        (*pointer).attr  same as ->  (-> is shorthand)

Python: None
C++:    nullptr (not NULL, not 0 — use nullptr in modern C++)

5. CP Usage
Binary tree node (LeetCode standard):
cppstruct TreeNode {
    int val;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

// Traversal
void inorder(TreeNode* root) {
    if (root == nullptr) return;
    inorder(root->left);
    cout << root->val << " ";
    inorder(root->right);
}
Linked list node:
cppstruct ListNode {
    int val;
    ListNode* next;
    ListNode(int x) : val(x), next(nullptr) {}
};
In Codeforces problems, you rarely use raw pointers. You simulate trees/graphs with arrays/vectors of indices. Pointers are more LeetCode territory.

6. Code Snippets
cpp// Swap two numbers using pointers (educational)
void swap(int* a, int* b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}
// But in CP just use std::swap(a, b)

// Dynamic array (just use vector instead)
int* arr = new int[n];
// ... use arr ...
delete[] arr;
// → Just use vector<int> arr(n) in CP

// Linked list insert at head
ListNode* insert(ListNode* head, int val) {
    ListNode* node = new ListNode(val);
    node->next = head;
    return node;
}

7. Common Mistakes
MISTAKE 1: Dereferencing null pointer
int* p = nullptr;
*p = 5;   // segfault — program crashes

MISTAKE 2: Dangling pointer
int* p;
{
    int x = 5;
    p = &x;
}  // x is destroyed here
*p = 10;  // undefined behavior!

MISTAKE 3: Using . instead of ->
Node* n = new Node(5);
n.val   // compile error — n is pointer!
n->val  // ✓

MISTAKE 4: Memory leak in CP (usually fine to ignore)
// new without delete → memory leak
// In CP with 1-2 second runtime, rarely causes issues

MISTAKE 5: NULL vs nullptr
int* p = NULL;    // old C style, avoid
int* p = nullptr; // ✓ modern C++

8. Memory Tricks

& = "address of" — &x gives where x lives in memory
* = "value at" — *p gives what's stored at address p
-> = "pointer dot" — ptr->val = (*ptr).val
nullptr = C++'s None — null pointer
new = creates on heap, returns pointer — like Python's object creation
In CP: avoid raw pointers when possible — use vectors/indices to simulate structures


9. Practice Tasks
Task 1: Implement a function void swapPtrs(int* a, int* b) that swaps two integers.
Task 2: Build a binary tree from array and do inorder traversal using recursive function with TreeNode*.
Task 3: Reverse a linked list using pointers.

10. Mini Revision Sheet — Module 11
┌──────────────────────────────────────────────────────────┐
│  int* p = &x;    → p stores address of x                │
│  *p              → dereference (get value at address)    │
│  ptr->member     → access member via pointer            │
│  nullptr         → null pointer (Python's None)          │
│  new Node(val)   → heap allocation, returns pointer      │
│  int& ref = x    → reference = alias (always valid)     │
│  In CP: prefer vector indices over raw pointers          │
│  LeetCode uses TreeNode* and ListNode* heavily           │
│  Codeforces: simulate trees with vector<int> adj[N]      │
└──────────────────────────────────────────────────────────┘


MODULE 12: Recursion

1. Concept Overview
Recursion in C++ is syntactically identical to Python. The differences are: stack size limits are smaller in C++, base cases are critical, and memoization uses arrays instead of @lru_cache. This is the foundation of DFS, divide & conquer, and DP.

2. Python vs C++ Mapping
PYTHON                          C++
──────                          ───
def fib(n):                     int fib(int n) {
    if n <= 1: return n             if (n <= 1) return n;
    return fib(n-1) + fib(n-2)     return fib(n-1) + fib(n-2);
                                }

@lru_cache(None)                int memo[100005];
def fib(n):                     int fib(int n) {
    ...                             if (memo[n] != -1) return memo[n];
                                    return memo[n] = fib(n-1) + fib(n-2);
                                }

sys.setrecursionlimit(100000)   // No easy fix — use iterative or increase stack

3. Syntax & Usage
cpp// Basic recursion
int factorial(int n) {
    if (n == 0) return 1;   // base case
    return n * factorial(n - 1);
}

// Fibonacci with memoization
int memo[100005];
int fib(int n) {
    if (n <= 1) return n;
    if (memo[n] != -1) return memo[n];
    return memo[n] = fib(n - 1) + fib(n - 2);
}

// Initialize memo:
memset(memo, -1, sizeof(memo));

// DFS on graph
vector<int> adj[100005];
bool visited[100005];

void dfs(int node) {
    visited[node] = true;
    cout << node << " ";
    for (int neighbor : adj[node]) {
        if (!visited[neighbor]) {
            dfs(neighbor);
        }
    }
}

// Recursive binary search
int binarySearch(vector<int>& a, int lo, int hi, int target) {
    if (lo > hi) return -1;
    int mid = lo + (hi - lo) / 2;  // avoids overflow vs (lo+hi)/2
    if (a[mid] == target) return mid;
    if (a[mid] < target) return binarySearch(a, mid+1, hi, target);
    return binarySearch(a, lo, mid-1, target);
}

4. Key Differences from Python
Python: default recursion limit = 1000 (increase with sys.setrecursionlimit)
C++:    stack is typically ~1MB → ~10^4 to 10^5 recursive calls max

Python: @lru_cache → automatic memoization
C++:    manual memo array or map, initialized with memset

Python: no tail call optimization
C++:    no TCO either — deep recursion = stack overflow in both

In CP:
- If n > 10^5, avoid recursion or convert to iterative
- Global memo arrays are faster than unordered_map memo
- memset(arr, -1, sizeof(arr)) sets all bytes to 0xFF = -1 for int
  (works for -1 and 0, not other values)

5. CP Usage
cpp// Tree traversal (classic recursion)
void dfs(int node, int parent, vector<int> adj[]) {
    for (int child : adj[node]) {
        if (child != parent) {
            dfs(child, node, adj);
        }
    }
}

// Subset generation
void subsets(int idx, vector<int>& a, vector<int>& curr) {
    if (idx == a.size()) {
        // process curr subset
        return;
    }
    curr.push_back(a[idx]);
    subsets(idx + 1, a, curr);   // include a[idx]
    curr.pop_back();
    subsets(idx + 1, a, curr);   // exclude a[idx]
}

// DP with memoization — top-down
int dp[1005][1005];
int solve(int i, int j) {
    if (/* base case */) return 0;
    if (dp[i][j] != -1) return dp[i][j];
    return dp[i][j] = /* transition */;
}

6. Code Snippets
cpp// memset patterns
memset(arr, -1, sizeof(arr));   // fill with -1
memset(arr, 0, sizeof(arr));    // fill with 0
memset(arr, 0x3f, sizeof(arr)); // fill with large value (~1e9) for "infinity"

// C++ "infinity" for DP
const int INF = 1e9;
const int INF = 0x3f3f3f3f;   // hex INF — commonly used

// Recursive power
ll power(ll base, ll exp, ll mod) {
    if (exp == 0) return 1;
    ll half = power(base, exp/2, mod);
    if (exp % 2 == 0) return half * half % mod;
    return base * half % half % mod;
}

// Count ways — classic recursion
int countWays(int n) {
    if (n == 0) return 1;
    if (n < 0) return 0;
    return countWays(n-1) + countWays(n-2);
}

7. Common Mistakes
MISTAKE 1: Stack overflow on large n
fib(100000) → stack overflow! (10^5 recursive calls too deep)
Fix: convert to iterative DP

MISTAKE 2: Not initializing memo
int memo[N];  // garbage values! some might accidentally equal valid answers
memset(memo, -1, sizeof(memo));  // ✓

MISTAKE 3: Wrong memset for non -1/0 values
memset(arr, 5, sizeof(arr));  // does NOT fill with 5! (fills bytes with 0x05)
// Only use memset for -1 (0xFF...FF) and 0 (0x00...00)

MISTAKE 4: Forgetting base case
int fib(int n) {
    return fib(n-1) + fib(n-2);  // infinite recursion!
}

MISTAKE 5: Mid calculation overflow
int mid = (lo + hi) / 2;   // lo + hi can overflow!
int mid = lo + (hi - lo) / 2;  // ✓

8. Memory Tricks

memset(arr, -1, sizeof(arr)) — "set memo to -1 before recursion"
Base case first — "always write base case before recursive case"
if (dp[i][j] != -1) return dp[i][j] — the memoization pattern, one line
mid = lo + (hi-lo)/2 — "lo plus half the gap" — overflow-safe mid
For deep recursion → convert to iterative (bottom-up DP)
0x3f3f3f3f — CP infinity (~10^9), adding two of them doesn't overflow int


9. Practice Tasks
Task 1: Fibonacci with memoization. Handle n up to 10^6 (use iterative if recursion is too deep).
Task 2: Generate all subsets of array [1,2,3,4]. Print each subset.
Task 3: Count number of ways to climb N stairs (1 or 2 steps at a time) mod 10^9+7.

10. Mini Revision Sheet — Module 12
┌──────────────────────────────────────────────────────────┐
│  Base case first, always                                 │
│  memset(memo, -1, sizeof(memo)) → init memoization      │
│  if (dp[i] != -1) return dp[i] → memo check             │
│  return dp[i] = expression     → memo store + return    │
│  Mid = lo + (hi-lo)/2          → overflow-safe          │
│  0x3f3f3f3f ≈ 10^9             → infinity constant      │
│  Stack limit ~10^4-10^5 calls  → deep recursion → TLE   │
│  Use iterative DP for n > 10^5                           │
│  DFS: visited[] + recursive call on unvisited neighbors  │
└──────────────────────────────────────────────────────────┘


MODULE 13: Time Complexity — Python vs C++

1. Concept Overview
The real reason you're learning C++ for CP: C++ executes ~10–100x faster than Python. This completely changes what algorithms are feasible. Knowing this lets you pick the right approach and estimate if your solution will pass within the time limit.

2. The Core Speed Difference
Operation           Python (ops/sec)    C++ (ops/sec)
─────────────────   ────────────────    ─────────────
Simple loop         ~10^7               ~10^8 – 10^9
Integer arithmetic  ~10^7               ~10^9
Array access        ~10^7               ~10^9
Function call       ~10^6               ~10^8

Rule of thumb:
Python can do ~10^7 simple operations per second
C++ can do ~10^8 to 10^9 simple operations per second

3. What Can Each Language Handle?
n = input size, time limit = 1 second (typical)

Algorithm       Complexity   Max n (Python)   Max n (C++)
──────────────  ──────────   ──────────────   ───────────
Brute force     O(n^2)       ~3,000           ~30,000
Cubic           O(n^3)       ~200             ~2,000
nlogn (sort)    O(n log n)   ~300,000         ~10^7
Linear          O(n)         ~10^6            ~10^8
Log             O(log n)     any              any

Verdict:
- Problem with n=10^5, O(n^2) → Python: TLE   C++: AC
- Problem with n=10^6, O(n log n) → Python: TLE   C++: AC
- Problem with n=10^8, O(n) → Python: TLE   C++: barely AC

4. Estimation Formula (For Contests)
C++ does ~10^8 simple ops/second

Your algorithm complexity: O(f(n))
With n = [problem input size]

If f(n) < 10^8 → likely AC (green light)
If f(n) ~ 10^8 → tight, optimize constants
If f(n) > 10^9 → TLE, need better algorithm

EXAMPLES:
n = 10^5, O(n^2) = 10^10 → TLE ✗
n = 10^5, O(n log n) = 10^5 * 17 ≈ 2*10^6 → AC ✓
n = 10^6, O(n) = 10^6 → AC ✓
n = 10^3, O(n^3) = 10^9 → tight
n = 20, O(2^n) = 10^6 → AC ✓

5. STL Complexity Cheat Sheet
Structure           Operation       Complexity
──────────────────  ──────────────  ──────────
vector              access          O(1)
vector              push_back       O(1) amortized
vector              insert/erase    O(n)
set / map           insert          O(log n)
set / map           find            O(log n)
unordered_set/map   insert/find     O(1) avg
priority_queue      push/pop        O(log n)
sort()              —               O(n log n)
binary_search       —               O(log n)

6. Python vs C++ — Real CP Examples
Problem: Sum of all pairs, n=10^4 (O(n^2) = 10^8)
Python: ~10 seconds → TLE
C++: ~0.1 seconds → AC

Problem: Sort n=10^6 numbers
Python: ~3 seconds → TLE
C++: ~0.3 seconds → AC

Problem: BFS on graph, n=10^5
Python: ~1 second → borderline TLE
C++: ~0.05 seconds → AC

Problem: Simple greedy, n=10^3
Python: fast enough
C++: same, but safer

7. Memory Complexity Notes
C++ int array of n=10^7 → 40MB (int = 4 bytes)
C++ long long array of n=10^7 → 80MB (ll = 8 bytes)

Typical CP memory limit: 256MB

Safe array sizes:
int arr[10^7]   → 40MB ✓
int arr[10^8]   → 400MB ✗ (exceeds limit!)
ll arr[5*10^6]  → 40MB ✓

Rule: n * size_of_type < 200MB (safe margin)

8. Code Snippet — Timer Template
cpp// Stress test your solution's speed
#include <bits/stdc++.h>
using namespace std;

int main() {
    auto start = chrono::high_resolution_clock::now();
    
    // your code here
    long long sum = 0;
    for (int i = 0; i < 1e8; i++) sum += i;
    
    auto end = chrono::high_resolution_clock::now();
    double time = chrono::duration<double>(end - start).count();
    cerr << "Time: " << time << "s\n";
    
    return 0;
}

9. Mini Revision Sheet — Module 13
┌──────────────────────────────────────────────────────────┐
│  C++ does ~10^8 ops/sec (Python: ~10^7)                  │
│  f(n) < 10^8 → AC in C++                                │
│  n=10^5 → O(n^2) = TLE, O(nlogn) = AC                  │
│  n=10^6 → O(n) = AC, O(nlogn) = AC                     │
│  n=10^3 → O(n^3) = tight (10^9)                         │
│  n=20   → O(2^n) = AC (2^20 = 10^6)                    │
│  set/map → O(log n),  unordered → O(1) avg              │
│  Memory: int[10^7] = 40MB, ll[10^7] = 80MB              │
│  256MB limit → max ~6*10^7 long longs                   │
└──────────────────────────────────────────────────────────┘


MODULE 14: Templates for CP (Boilerplate)

1. Concept Overview
In CP, you lose precious minutes writing boilerplate. A solid template means you hit "run" faster. Here are multiple levels of templates — pick one and memorize it cold.

2. Level 1 — Minimal (Beginners)
cpp#include <bits/stdc++.h>
using namespace std;
typedef long long ll;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    int t;
    cin >> t;
    while (t--) {
        // solve
    }
    return 0;
}

3. Level 2 — Standard (Most Contests)
cpp#include <bits/stdc++.h>
using namespace std;

typedef long long ll;
typedef pair<int,int> pii;
typedef pair<ll,ll> pll;
typedef vector<int> vi;
typedef vector<ll> vll;

#define pb push_back
#define all(v) (v).begin(), (v).end()
#define sz(v) (int)(v).size()
#define F first
#define S second
#define MOD 1000000007LL
#define INF 1e18

void solve() {
    int n;
    cin >> n;
    
    // your solution
    
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    int t = 1;
    cin >> t;
    while (t--) solve();
    
    return 0;
}

4. Level 3 — Advanced (Competitive)
cpp#include <bits/stdc++.h>
using namespace std;

// Types
typedef long long ll;
typedef unsigned long long ull;
typedef pair<int,int> pii;
typedef pair<ll,ll> pll;
typedef vector<int> vi;
typedef vector<ll> vll;
typedef vector<pii> vpii;

// Macros
#define pb push_back
#define eb emplace_back
#define all(v) (v).begin(), (v).end()
#define rall(v) (v).rbegin(), (v).rend()
#define sz(v) (int)(v).size()
#define F first
#define S second
#define yes cout << "YES\n"
#define no  cout << "NO\n"

// Constants
const ll MOD = 1e9 + 7;
const ll INF = 1e18;
const int MAXN = 2e5 + 5;
const double PI = acos(-1.0);

// Useful functions
ll gcd(ll a, ll b) { return b ? gcd(b, a%b) : a; }
ll lcm(ll a, ll b) { return a / gcd(a, b) * b; }
ll power(ll b, ll e, ll m = MOD) {
    ll r = 1; b %= m;
    for (; e > 0; e >>= 1) {
        if (e & 1) r = r * b % m;
        b = b * b % m;
    }
    return r;
}

void solve() {
    int n;
    cin >> n;
    
    // solution here
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    int t = 1;
    cin >> t;
    while (t--) solve();
    
    return 0;
}

5. Graph Template Add-On
cpp// Add to template when solving graph problems
const int MAXN = 2e5 + 5;
vector<int> adj[MAXN];
bool visited[MAXN];

void dfs(int u) {
    visited[u] = true;
    for (int v : adj[u])
        if (!visited[v]) dfs(v);
}

void bfs(int start) {
    queue<int> q;
    q.push(start);
    visited[start] = true;
    while (!q.empty()) {
        int u = q.front(); q.pop();
        for (int v : adj[u]) {
            if (!visited[v]) {
                visited[v] = true;
                q.push(v);
            }
        }
    }
}

6. DP Template Add-On
cpp// 1D DP
vector<ll> dp(n + 1, 0);
dp[0] = 1;
for (int i = 1; i <= n; i++) {
    // transition
}

// 2D DP
vector<vector<ll>> dp(n + 1, vector<ll>(m + 1, 0));

// Memoized recursion
int memo[1005][1005];
memset(memo, -1, sizeof(memo));
function<int(int,int)> solve = [&](int i, int j) -> int {
    if (/* base */) return 0;
    if (memo[i][j] != -1) return memo[i][j];
    return memo[i][j] = /* transition */;
};

7. Mini Revision Sheet — Module 14
┌──────────────────────────────────────────────────────────┐
│  ALWAYS: #include<bits/stdc++.h>, using namespace std;   │
│  ALWAYS: ios_base::sync_with_stdio(false); cin.tie(NULL) │
│  ALWAYS: typedef long long ll; (at minimum)              │
│  #define all(v) v.begin(),v.end() → saves chars         │
│  void solve() + while(t--) solve() → clean structure    │
│  Keep template in a file/IDE snippet — paste on day 1   │
│  gcd, power → define once, use forever                   │
│  #define yes/no → common in boolean answer problems      │
└──────────────────────────────────────────────────────────┘


MODULE 15: Advanced STL (priority_queue, deque, etc.)

1. Concept Overview
These are the power tools. Once you know vectors, sets, and maps, these structures let you solve problems in optimal time that would be impossible otherwise. Each has a specific use case — know when to reach for which one.

2. Priority Queue (Max Heap by Default)
Python: heapq (min heap only)
C++:    priority_queue (max heap by default!)

Python heapq          C++ priority_queue
──────────────        ─────────────────────────────
heapq.heappush(h,x)   pq.push(x)
heapq.heappop(h)      pq.top(); pq.pop();  (two steps!)
h[0]                  pq.top()
len(h)                pq.size()
heapq.heappush(h,-x)  priority_queue<int,vector<int>,greater<int>> pq;
(for min heap)        (for min heap — verbose but that's C++)
cpp// MAX heap (default)
priority_queue<int> pq;
pq.push(3);
pq.push(1);
pq.push(5);
cout << pq.top();  // 5 (max element)
pq.pop();          // removes 5
cout << pq.top();  // 3

// MIN heap — Python's default heapq behavior
priority_queue<int, vector<int>, greater<int>> pq;
pq.push(3); pq.push(1); pq.push(5);
cout << pq.top();  // 1 (min element)

// Priority queue of pairs (sorts by first element)
priority_queue<pair<int,int>> pq;
pq.push({3, 'a'});
pq.push({1, 'b'});
// pq.top() = {3, 'a'} (max by first element)

// Dijkstra pattern (min heap of {dist, node})
priority_queue<pii, vector<pii>, greater<pii>> pq;
pq.push({0, source});
while (!pq.empty()) {
    auto [dist, u] = pq.top(); pq.pop();
    // relax edges from u
}

3. Deque (Double-Ended Queue)
Python: collections.deque  →  C++: deque<int>

Python                      C++
──────                      ───
dq.append(x)                dq.push_back(x)
dq.appendleft(x)            dq.push_front(x)
dq.pop()                    dq.pop_back()
dq.popleft()                dq.pop_front()
dq[0]                       dq.front()
dq[-1]                      dq.back()
cppdeque<int> dq;
dq.push_back(3);
dq.push_front(1);
dq.push_back(5);
// dq = {1, 3, 5}
cout << dq.front();   // 1
cout << dq.back();    // 5
dq.pop_front();
// dq = {3, 5}
Key CP use: Sliding Window Maximum (monotonic deque)
cpp// Maximum in every window of size k
vector<int> maxSliding(vector<int>& a, int k) {
    deque<int> dq;  // stores indices, front = max
    vector<int> res;
    for (int i = 0; i < a.size(); i++) {
        if (!dq.empty() && dq.front() < i - k + 1) dq.pop_front();
        while (!dq.empty() && a[dq.back()] <= a[i]) dq.pop_back();
        dq.push_back(i);
        if (i >= k - 1) res.push_back(a[dq.front()]);
    }
    return res;
}

4. Stack & Queue
cpp// Stack (LIFO) — Python: list with append/pop
stack<int> st;
st.push(1); st.push(2); st.push(3);
cout << st.top();   // 3 (top, not popped)
st.pop();           // removes 3
st.empty();         // false

// Queue (FIFO) — Python: collections.deque
queue<int> q;
q.push(1); q.push(2); q.push(3);
cout << q.front();  // 1
cout << q.back();   // 3
q.pop();            // removes front (1)
q.empty();          // false

5. Multiset & Multimap
cpp// multiset — like set but allows duplicates
multiset<int> ms;
ms.insert(3); ms.insert(3); ms.insert(1);
// ms = {1, 3, 3}

ms.erase(ms.find(3));  // removes ONE occurrence of 3
// ms = {1, 3}

ms.erase(3);  // removes ALL occurrences of 3 — careful!

ms.count(3);  // how many 3s exist

// Use case: maintain sorted multiset, find kth element, etc.

6. Bitset
cpp// Fixed-size bit array — extremely fast for bitmask DP
bitset<1000> bs;
bs.set(3);      // set bit 3
bs.reset(3);    // clear bit 3
bs.flip(3);     // toggle bit 3
bs[3];          // access bit 3
bs.count();     // count set bits
bs.any();       // any bit set?
bs.none();      // no bits set?

// Bitwise operations on entire bitset — O(n/64) not O(n)!
bitset<1000> a, b;
auto c = a & b;   // AND
auto d = a | b;   // OR
auto e = a ^ b;   // XOR

7. CP Patterns with Advanced STL
cpp// Kth largest element with priority_queue
priority_queue<int, vector<int>, greater<int>> minHeap;
for (int x : arr) {
    minHeap.push(x);
    if (minHeap.size() > k) minHeap.pop();
}
cout << minHeap.top();  // kth largest

// Running median with two heaps
priority_queue<int> lower;          // max heap (lower half)
priority_queue<int, vector<int>, greater<int>> upper;  // min heap (upper half)
// Push to lower, balance between them

// Monotonic stack — next greater element
stack<int> st;
vector<int> res(n, -1);
for (int i = 0; i < n; i++) {
    while (!st.empty() && a[st.top()] < a[i]) {
        res[st.top()] = a[i];
        st.pop();
    }
    st.push(i);
}

8. Quick Reference Table
Structure         Python equiv        Best for
──────────────    ──────────────      ────────────────────────────
priority_queue    heapq               Dijkstra, kth element, greedy
deque             collections.deque   Sliding window, BFS
stack             list                Monotonic stack, DFS, brackets
queue             collections.deque   BFS
multiset          sorted list         Order stats, duplicate sorted
bitset            —                   Bitmask DP, set operations

9. Common Mistakes
MISTAKE 1: priority_queue top() without pop()
pq.top();   // just peeks
pq.pop();   // must call separately to remove (unlike heappop!)

MISTAKE 2: Default is MAX heap (opposite of Python's heapq!)
priority_queue<int> pq;  // MAX heap — Python's heapq is MIN!
// For min heap in C++: priority_queue<int,vector<int>,greater<int>> pq;

MISTAKE 3: Erasing all copies in multiset
ms.erase(3);    // erases ALL 3s!
ms.erase(ms.find(3));  // erases only ONE 3 ✓

MISTAKE 4: queue vs deque
queue<int> q;   // FIFO only (push back, pop front)
deque<int> dq;  // both ends — use when you need front push/pop

MISTAKE 5: Stack doesn't support iteration
for (int x : st) { }  // compile error! stack has no iterators
// Use vector as stack instead if you need to iterate

10. Mini Revision Sheet — Module 15
┌──────────────────────────────────────────────────────────┐
│  priority_queue = MAX heap (Python heapq = min!)         │
│  Min heap: priority_queue<int,vector<int>,greater<int>>  │
│  pq.top() peek; pq.pop() remove (two separate calls!)   │
│  deque: push/pop from both ends — sliding window         │
│  stack: top(), push(), pop() — LIFO                      │
│  queue: front(), push(), pop() — FIFO                    │
│  multiset: sorted with duplicates, erase one: find()    │
│  bitset<N>: ultra-fast bit ops, count(), any(), none()  │
│  Dijkstra → min heap of {dist, node}                     │
│  Kth largest → min heap of size k                        │
└──────────────────────────────────────────────────────────┘


🏁 COMPLETE PROGRESSION SUMMARY
┌─────────────────────────────────────────────────────────────┐
│           YOUR C++ CP ROADMAP — COMPLETE                    │
├────┬────────────────────────────┬───────────────────────────┤
│ #  │ Module                     │ Key Takeaway              │
├────┼────────────────────────────┼───────────────────────────┤
│ 1  │ Basic Syntax + I/O         │ cin/cout, "\n" not endl   │
│ 2  │ Data Types                 │ int vs ll, overflow kills │
│ 3  │ Operators                  │ no **, /=int div, &&/||   │
│ 4  │ Conditionals & Loops       │ {}, else if, for 3-part   │
│ 5  │ Functions                  │ & param, void, typed      │
│ 6  │ Arrays & Strings           │ substr(start,len), freq[] │
│ 7  │ Vectors ⭐                 │ push_back, all(), size()  │
│ 8  │ STL: set/map/pair ⭐       │ sorted!, count(), m[k]++  │
│ 9  │ Sorting + Comparator ⭐    │ lambda, strict <, [&]     │
│ 10 │ Fast I/O + Macros ⭐       │ sync_false, template      │
│ 11 │ Pointers                   │ ->, nullptr, new          │
│ 12 │ Recursion                  │ memset, memo[], base case │
│ 13 │ Time Complexity            │ C++: 10^8/sec, plan ahead │
│ 14 │ CP Templates               │ paste ready, never retype │
│ 15 │ Advanced STL ⭐            │ pq=MAX heap!, deque, mono │
└────┴────────────────────────────┴───────────────────────────┘
⭐ = Master these first, highest contest ROI