# cpp_coding_guidelines
List of rules I generally follow while writing the software in cpp. Think of this as best coding practices.

### Last updated :  13th October, 2024
> [!WARNING]  
 This is a work in progress, I am trying to compile all the rules and guidelines into one single repo, so repo keeps changing.

>[!Caution]
Also you might notice few mistakes in the code w.r.t best practices which will be resolved in upcoming rules. Like `rule 1` to `rule 3` will not have a return statement for main which will be explained in `rule 4`.

<details>
 <summary> 
 1. Initalize all objects and variables with a value, using {} operator forces default constructor to be invoked or assigns `0` to variables. 
 </summary>

🔗[godbolt](https://godbolt.org/z/jbdd45eWW)

```C++
 // Rule 1: Init all variables and objects
#include<iostream>
class Sensor{
    int adcvalue;
    public:
    Sensor(){
        this->adcvalue=50;
    }
    Sensor(int offset_p): adcvalue{offset_p}{
        ;
    }
    int get_adcvalue(){
        return adcvalue;
    }
};
int main(){
    int unknown_variable;
    std::cout<<"Junk value is "<<unknown_variable;
    int properly_init_variable{100};
    std::cout<<"\nProperly init value is "<<properly_init_variable;
    // same thing to classes 
    Sensor obj_sensor = {}; // default constructor will be called
    std::cout<<"\nAdc value: "<<obj_sensor.get_adcvalue();
}
```
 </details>

 <details>
 <summary> 
 2. Don't use magic numbers.
 </summary>

[godbolt](https://godbolt.org/z/nWYPWM6TE)

```c++
// Rule 2: Don't use magic numbers.
#include<iostream>
int main(){
    float pi{3.14f}, radius_in_cm{8.0f};
    // instead of calculating area like this
    float area {3.14*8*8};
    // always prefer this
    float proper_area {pi*radius_in_cm*radius_in_cm};
}
```