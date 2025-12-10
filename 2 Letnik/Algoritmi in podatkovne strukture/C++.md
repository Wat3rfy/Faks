
**Headers**

Importanje headerjev 

```cpp
#include <iostream>; // standard libraries
#include "someLibrary"; // custom libraries
```

Pomembni headerji:
```
<iostream> cout cin cerr clog

<fstream> ifstream (inputfilestream) ofstream (output filestream)
```

```
<vector> dynamic array
<string> string
<map> associative array
<unordered_map> hash table
```


***
**Pisanje**

| Operacija | Objekt/Funkcija | Glava | Uporaba |
| :--- | :--- | :--- | :--- |
| **Standardni Izpis** | `std::cout <<` | `<iostream>` | Izpis na konzolo. |
| **Standardni Vnos** | `std::cin >>` | `<iostream>` | Branje ene besede/vrednosti. |
| **Branje Vrstice** | `std::getline(std::cin, str)` | `<iostream>` | Branje celotne vrstice, vključno s presledki. |
| **Pisanje v datoteko** | `std::ofstream` | `<fstream>` | Ustvarjanje in pisanje v datoteke. |
| **Branje iz datoteke** | `std::ifstream` | `<fstream>` | Branje iz obstoječih datotek. |
| **Formatiranje** | `std::setprecision`, `std::setw` | `<iomanip>` | Natančno določanje oblike izpisa. |

****
**Namespace**

V C++ lahko definiramo več funkcij z istim imenom v drugih imenskih prostorih.
```cpp
namespace nsA{
	int funkcija();
}
namespace nsB{
	int funkcija();
}

nsA::funkcija(); // uporablja iz nsA
nsB::funkcija(); // uporablja iz nsA

using nsA::funkcija; // vpeljes samo to definicijo funkcije
using namespace nsA; // vpelje vse definicije v nsA
```

***
**Strings**

| Feature | Description |
| :--- | :--- |
| **Header** | `<string>` |
| **Type** | `std::string` (part of the C++ Standard Library, usually implemented as a dynamic array of characters) |
| **Initialization** | `std::string s = "hello";` |
| **Size/Length** | `s.length()` or `s.size()` (returns the number of characters) |
| **Concatenation** | Use the `+` operator: `s1 + s2` |
| **Access** | `s[i]` (for character access, like arrays) |
| **Mutability** | Mutable (can be changed after creation) |
| **Compatibility**| Easily convertible to C-style strings (`const char*`) using `s.c_str()` |
| **Key Advantage**| Handles memory management automatically (no manual `malloc`/`free` needed) |

***
**Pairs**

A `std::pair` in C++ is a simple container that holds exactly two heterogeneous elements (which can be of different types, e.g., an `int` and a `string`).

It is defined in the `<utility>` header.

---

**Key Characteristics**

| Feature | Description |
| :--- | :--- |
| Fixed Size | Always holds exactly two elements. |
| Heterogeneous | The two elements can be of different data types. |
| Access | Elements are accessed using `.first` and `.second`. |


*   **Direct Initialization**
    You can initialize a pair directly using the types:
    ```cpp
    // Pair of an integer and a string
    std::pair<int, std::string> p1 (10, "Apple");

    // Accessing elements
    std::cout << p1.first << " is " << p1.second << std::endl;
    ```

*   **Using `std::make_pair` (Type Deduction)**
    `std::make_pair` automatically deduces the types:
    ```cpp
    std::pair<double, bool> p2 = std::make_pair(3.14, true);

    std::cout << p2.first << " and " << p2.second << std::endl;
    ```

*   **Using Braced Initialization (C++11 and later)**
    This is the most modern and concise way:
    ```cpp
    std::pair<char, int> p3 {'A', 5};
    ```

**Common Use Cases**

*   **Returning Multiple Values**
    A function can use a pair to return two related pieces of data:
    ```cpp
    std::pair<int, bool> process_data(int input) {
        if (input > 0) {
            return {input * 2, true};
        }
        return {0, false};
    }
    ```

*   **Keys in Mappings**
    Pairs are internally used by associative containers like `std::map` to store the key and value:
    ```cpp
    std::map<std::string, int> ages;

    // Inserting using a pair
    ages.insert(std::pair<std::string, int>("Alice", 30));
    ```

*   **Storing Coordinates**
    If you need to store simple (x, y) coordinates:
    ```cpp
    std::pair<int, int> coordinates (100, 200);
    ```

**Summary of Accessors**

| Accessor | Type | Example |
| :--- | :--- | :--- |
| `.first` | Type 1 | `p.first = 5;` |
| `.second` | Type 2 | `p.second = "Hello";` |


***

**Vectors**



To use `std::vector`, you must include the `<vector>` header.

### Basic Setup

```cpp
#include <vector>
#include <iostream>

int main() {
    // 1. Declare an empty vector of integers
    std::vector<int> numbers; 

    // 2. Declare and initialize with values (Initializer List)
    std::vector<std::string> names = {"Alice", "Bob", "Charlie"};

    // 3. Declare with size and default value (as discussed before)
    std::vector<double> scores(10, 0.0); // 10 elements, all initialized to 0.0

    // 4. Declare with size (elements are default-initialized: 0 for int, etc.)
    std::vector<int> default_init(5); // 5 elements, typically all 0
    
    return 0;
}
```


Vectors grow dynamically by adding elements to the back.

| Method | Description |
| :--- | :--- |
| **`push_back(value)`** | Adds a new element to the end of the vector. (Most common way to grow a vector.) |
| **`pop_back()`** | Removes the element at the end of the vector. (Does NOT return the value.) |
| **`insert(position, value)`** | Inserts an element *before* the specified position (iterator). Slow operation. |
| **`erase(position)`** | Removes the element at the specified position (iterator). Slow operation. |
| **`clear()`** | Removes all elements from the vector (size becomes 0). |

**Example:**

```cpp
std::vector<int> v;

v.push_back(10); // v: {10}
v.push_back(20); // v: {10, 20}
v.push_back(30); // v: {10, 20, 30}

v.pop_back();    // v: {10, 20}

// Inserting an element at the beginning (before v.begin())
v.insert(v.begin(), 5); // v: {5, 10, 20} 

// Erasing the second element (at index 1)
v.erase(v.begin() + 1); // v: {5, 20}
```



| Method | Description | Warning |
| :--- | :--- | :--- |
| **`v[index]`** | Accesses the element at the given index. (Fastest access.) | **No bounds checking.** If the index is out of range, the behavior is undefined. |
| **`v.at(index)`** | Accesses the element at the given index. | **Throws `std::out_of_range` exception** if the index is invalid (safer). |
| **`v.front()`** | Returns a reference to the first element. | Undefined if the vector is empty. |
| **`v.back()`** | Returns a reference to the last element. | Undefined if the vector is empty. |


These methods help you manage the memory usage and current state of the vector:

| Method | Description |
| :--- | :--- |
| **`v.size()`** | Returns the number of elements currently in the vector. |
| **`v.empty()`** | Returns `true` if the vector has zero elements. |
| **`v.capacity()`** | Returns the total number of elements the vector can hold *before* resizing/reallocating memory. |
| **`v.reserve(n)`** | Explicitly requests that the vector allocate memory for at least `n` elements. (Useful for performance if you know the final size.) |
| **`v.resize(n)`** | Changes the size of the vector to `n`. If `n` is smaller, elements are removed. If `n` is larger, new elements are added (initialized to default value, e.g., 0). |

The best way to read all elements in a vector is using a loop.

### A. Range-Based For Loop (Modern C++)

This is the preferred, safest, and most concise method.

```cpp
std::vector<int> nums = {10, 20, 30};

for (int n : nums) {
    std::cout << n << " "; // Output: 10 20 30
}
```

### B. Index-Based For Loop (Traditional)

Useful when you need access to the index of the element.

```cpp
for (size_t i = 0; i < nums.size(); ++i) {
    std::cout << "Element " << i << ": " << nums[i] << "\n";
}
```

### C. Iterator-Based Loop (Advanced)

Used when interacting with standard library algorithms (like `std::fill`, `std::sort`, etc.).

```cpp
for (auto it = nums.begin(); it != nums.end(); ++it) {
    std::cout << *it << " "; // *it dereferences the iterator to get the value
}
```