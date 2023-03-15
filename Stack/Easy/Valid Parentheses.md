# [Valid Parentheses](https://leetcode.com/problems/valid-parentheses)
### Intuition:
The intuition behind this approach is that a closing parentheses must always match the most recently opened parentheses of the same type. So, we use a stack to keep track of the most recently opened parentheses of each type.

### Approach : 
- As we traverse the string, we push opening parentheses onto the stack and pop them off 
when we encounter the corresponding closing parentheses. 
- If the stack is empty when we encounter a closing parentheses, we know that it doesn't match any opening parentheses 
and hence the string is invalid. 
- Similarly, if the closing parentheses doesn't match the expected opening 
parentheses, we know that the string is invalid.
- If we have processed the entire stringand the stack is empty, we know that all parentheses have been matched and the string is valid.

**Test Case 1:** "[ ( ) ] ()" ==>
1. s='[' ,it will be into the stack so st = "["
2. s='(' ,it will be into the stack so st="[("
3. s=')' --> as st.size()>0 and st.top() = '(' , so '(' will be popped out from the stack --> st="["
4. s=']' -->as st.size()>0 and st.top() = '[' , so '[' will be popped out from the stack --> st=""
5. same will happen for '()' and the function will return **true** as the string is valid

**Test Case 2:** "[ ( ] )" ==>
1. s='[' ,it will be into the stack so st= "["
2. s='(',it will be into the stack so st="[("
3. Now s=']' and as st.size() >0  and st.top()!='[', so the function will return false 

**Code:**
#
```
class Solution {
public:
    bool isValid(string s) {
        stack <char> st;
        
        for(char c:s){
            if((c=='{' )|| (c=='(') || (c=='[')) st.push(c);
            else {
                if(st.size()==0) return false;
                else if(c==')' && st.size()>0 && st.top()!='(') return false;
                else if(c=='}' && st.size()>0 && st.top()!='{') return false;
                else if(c==']' && st.size()>0 && st.top()!='[') return false;
                else st.pop();
            }
        }
        // below condition is for cases like this --> s="[()[]"
        if(st.size()>0) return false;
        return true;
    }
};
```
