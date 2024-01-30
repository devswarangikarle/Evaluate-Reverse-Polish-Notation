# Evaluate-Reverse-Polish-Notation
You are given an array of strings tokens that represents an arithmetic expression in a Reverse Polish Notation.  Evaluate the expression. Return an integer that represents the value of the expression.  Note that:  The valid operators are '+', '-', '*', and '/'. Each operand may be an integer or another expression. 


class Solution:
    def resolves(self, a, b, Operator):
        if Operator == '+':
            return a + b
        elif Operator == '-':
            return a - b
        elif Operator == '*':
            return a * b
        return int(a / b)

    def evalRPN(self, tokens):
        stack = []
        for token in tokens:
            if len(token) == 1 and ord(token) < 48:
                integer2 = stack.pop()
                integer1 = stack.pop()
                operator = token
                resolved_ans = self.resolves(integer1, integer2, operator)
                stack.append(resolved_ans)
            else:
                stack.append(int(token))
        return stack.pop()

