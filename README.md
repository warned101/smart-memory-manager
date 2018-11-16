# smart-memory-manager
An easy way to deal with c++ pointers
Now you do not have to worry about memory leakage because of pointers...
you can easily instantiate your objects with `new` keyword and asign that object with a key(key must be of std::string type) to `SmartMemoryManager` class. Now use that object and don't worry about deleting them. `SmartMemoryManager` will automatically delete the object for you when it goes out of scope.
# Example
```
#include <smart_mem/smart_mem.h>
#include <iostream>
#include <string>
using namespace std;

class Demo {
  string name;
  public:
    Demo() { cout<<"constructor\n" }
    ~Demo() { cout<<"destructor\n" }
    Demo(string n) {name = n;}
    string get() { return name; }
};

int main() {
  SmartMemoryManager<Demo*> sm;
  Demo *d1 = new Demo("demo name 1");
  Demo *d2 = new Demo("demo name 2");
  sm.append("demo1",d1);
  sm.append("demo2",d2);
  sm.append("demo3",new Demo());
}
```
