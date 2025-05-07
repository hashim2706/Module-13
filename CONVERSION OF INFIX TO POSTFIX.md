# Exp.No:32  
## CONVERSION OF INFIX TO POSTFIX

---

### AIM  
To write a Python program to convert a given Infix expression to Postfix expression by following the precedence and associative rules. The input expression contains only Division, Subtraction, and Bitwise AND operators. A dictionary is used to set the priority for operators, and a set is used to hold the operators used in the given expression.

---

### ALGORITHM

1. **Start the program.**
2. **Initialize an empty stack** and an empty output string.
3. **Iterate through each character** in the infix expression:
   - If the character is **not an operator**, append it directly to the output string.
   - If the character is an **open parenthesis '('**, push it onto the stack.
   - If the character is a **close parenthesis ')'**, pop from the stack and append to the output until encountering a left parenthesis '('.
   - If the character is an **operator**, handle it based on precedence:
     - While there’s an operator at the top of the stack with higher or equal precedence, pop the stack and append those operators to the output.
     - Push the current operator onto the stack.
4. **Use a priority dictionary** to define operator precedence, ensuring higher precedence operators are placed before lower precedence ones.
5. Once the expression is fully processed, continue popping any remaining operators from the stack and append them to the output.
6. **Return the final postfix expression.**
7. **Print the result.**
8. **End the program.**

---

### PROGRAM

```python
Op = set(['+','*','+','(',')'])
pr= {'+':1,'*':2} 
 
 
def infixToPostfix(exp): 

    stack = [] 
    otp = '' 
    
    for char in exp:
        if char not in Op:
            otp+=char
        elif char=='(':
            stack.extend('(')
        elif char==')':
            while stack and stack[-1]!='(':
                otp+=stack.pop()
            stack.pop()
        else:
            while stack and stack[-1]!='('and pr[char]<=pr[stack[-1]]:
                otp+=stack.pop()
            stack.append(char)
    while stack:
        otp+=stack.pop()# Write your code here
    
    return otp
exp =input()
print('Infix notation: ',exp)

print('Postfix notation: ',infixToPostfix(exp))
```

### OUTPUT

![Screenshot 2025-05-02 195654](https://github.com/user-attachments/assets/4822f619-17a2-4ba6-b259-2bed798c5338)

### RESULT
Thus, the program executed successfully and the output is verified.
