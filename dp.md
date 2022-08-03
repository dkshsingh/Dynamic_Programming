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
#### 2. Bottom-up with Tabulation
        Tabulation is the opposite of the top-down approach and avoids recursion.In this approach, we solve the problem “bottom-up” (i.e. by solving all the related sub-problems first). This is typically done by filling up an n-dimensional table. Based on the results in the table, the solution to the top/original problem is then computed.
#### code:
      def calculateFibonacci(n):
          dp = [0, 1]
          for i in range(2, n + 1):
              dp.append(dp[i - 1] + dp[i - 2])

          return dp[n]


     def main():
         print("5th Fibonacci is ---> " + str(calculateFibonacci(5)))
         print("6th Fibonacci is ---> " + str(calculateFibonacci(6)))
         print("7th Fibonacci is ---> " + str(calculateFibonacci(7)))


     main()
### 0/1 Knapsack
     0/1 Knapsack pattern is based on the famous problem with the same name which is efficiently solved using Dynamic Programming (DP).
     After the recursive solution, we will modify our algorithm to apply advanced techniques of Memoization and Bottom-Up Dynamic Programming to develop a complete understanding of this pattern.
### 1. 0/1 Knapsack (medium)
     Given the weights and profits of ‘N’ items, we are asked to put these items in a knapsack with a capacity ‘C.’ The goal is to get the maximum profit out of the knapsack items. Each item can only be selected once, as we don’t have multiple quantities of any item.

### problem statement
     Let’s take Merry’s example, who wants to carry some fruits in the knapsack to get maximum profit. Here are the weights and profits of the fruits:
     
     Items: { Apple, Orange, Banana, Melon }
     Weights: { 2, 3, 1, 4 }
     Profits: { 4, 5, 3, 7 }
     Knapsack capacity: 5
   
    Let’s try to put various combinations of fruits in the knapsack, such that their total weight is not more than 5:
    Apple + Orange (total weight 5) => 9 profit
    Apple + Banana (total weight 3) => 7 profit
    Orange + Banana (total weight 4) => 8 profit
    Banana + Melon (total weight 5) => 10 profit
    
    This shows that Banana + Melon is the best combination as it gives us the maximum profit
    
### brute_force
     for each item 'i' 
    create a new set which INCLUDES item 'i' if the total weight does not exceed the 
     capacity, and recursively process the remaining capacity and items
    create a new set WITHOUT item 'i', and recursively process the remaining items 
    return the set from the above two sets with higher profit
### python code:
           def solve_knapsack(profits, weights, capacity):
               return knapsack_recursive(profits, weights, capacity, 0)


           def knapsack_recursive(profits, weights, capacity, currentIndex):
           # base checks
           if capacity <= 0 or currentIndex >= len(profits):
               return 0

           # recursive call after choosing the element at the currentIndex
           # if the weight of the element at currentIndex exceeds the capacity, we  shouldn't 
           # process this
               profit1 = 0
           if weights[currentIndex] <= capacity:
               profit1 = profits[currentIndex] + knapsack_recursive(profits, weights, capacity - weights[currentIndex], currentIndex + 1)

           # recursive call after excluding the element at the currentIndex
               profit2 = knapsack_recursive(profits, weights, capacity, currentIndex + 1)

           return max(profit1, profit2)


            def main():
                print(solve_knapsack([1, 6, 10, 16], [1, 2, 3, 5], 7))
                print(solve_knapsack([1, 6, 10, 16], [1, 2, 3, 5], 6))


            main()
