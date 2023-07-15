#include <stack>
#include <string>

class Solution {
public:
    /**
     * 
     * @param tokens string字符串vector 
     * @return int整型
     */
    int evalRPN(vector<string>& tokens) {
        // write code here
        std::stack<int> stk;
        for(string token : tokens){
            if(token != "+" && token != "-" && token != "*" && token != "/"){
                stk.push(std::stoi(token));
                continue;
            }
            int after_num = stk.top();
            stk.pop();
            int before_num = stk.top();
            stk.pop();
             if(token == "+"){
                 stk.push(before_num + after_num);
             }else if(token == "-"){
                 stk.push(before_num - after_num);
             }else if(token == "*"){
                 stk.push(before_num * after_num);
             }else if(token == "/"){
                 stk.push(before_num / after_num);
             }
        }
        return stk.top();
    }
};


-------------------------
* c++ string 转 int

在C++中，安全地将字符串转换为整数的方法是使用std::stringstream或std::stoi并捕获可能的异常。下面是两种方法的示例：

使用std::stringstream：
#include <iostream>
#include <sstream>
#include <string>

int main() {
    std::string str = "12345";
    std::stringstream ss(str);
    int num = 0;
    if ((ss >> num).fail()) 
    {
        // handle error
    } 
    else 
    {
        std::cout << num;
    }
    return 0;
}
使用std::stoi并捕获异常：
#include <iostream>
#include <string>

int main() {
    std::string str = "12345";
    try {
        int num = std::stoi(str);
        std::cout << num;
    } catch (std::invalid_argument const &e) {
        // if no conversion could be performed
    } catch (std::out_of_range const &e) {
        // if the converted value would fall out of the range of the result type 
    }

    return 0;
}
这两种方法都能安全地处理无法转换为整数的字符串，而不会导致程序崩溃或未定义的行为。

--------------------------
* c++ 的switch仅能作用于int
https://stackoverflow.com/questions/16388510/evaluate-a-string-with-a-switch-in-c