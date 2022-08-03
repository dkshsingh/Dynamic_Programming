# what is dynamic programmming?
    Dynamic Programming (DP) is an algorithmic technique for solving an optimization problem by breaking it down into simpler subproblems and utilizing the fact that the optimal solution to the overall problem depends upon the optimal solution to its subproblems.
    Let’s take the example of the Fibonacci numbers
    If we are asked to calculate the nth Fibonacci number, we can do that with the following equation,
###  
    Fib(n) = Fib(n-1) + Fib(n-2), for n > 1  
    
###  Characteristics of Dynamic Programming
####  1.Overlapping Subproblems
        Subproblems are smaller versions of the original problem, 
        Take the example of the Fibonacci numbers; to find the fib(4)
<img width="448" alt="d" src="https://user-images.githubusercontent.com/78050476/182662413-bcc93780-c3ff-43e1-bab8-e3bb8a003bd7.png">

####  2.Optimal Substructure Property
          Fib(n) = Fib(n-1) + Fib(n-2)
         
### Dynamic Programming Methods
#### 1. Top-down with Memoization
          we try to solve the bigger problem by recursively finding the solution to smaller sub-problems.
          Whenever we solve a sub-problem, we cache its result so that we don’t end up solving it repeatedly if it’s called multiple times. Instead, we can just return           the saved result. This technique of storing the results of already solved subproblems is called Memoization.
#### code:
          def calculateFibonacci(n):
              if n < 2:
                  return n

              return calculateFibonacci(n - 1) + calculateFibonacci(n - 2)


          def main():
              print("5th Fibonacci is ---> " + str(calculateFibonacci(5)))
              print("6th Fibonacci is ---> " + str(calculateFibonacci(6)))
              print("7th Fibonacci is ---> " + str(calculateFibonacci(7)))


          main()
