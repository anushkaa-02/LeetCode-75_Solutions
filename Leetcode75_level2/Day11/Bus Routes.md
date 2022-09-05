# Bus Routes
- ## Question:
>You are given an array routes representing bus routes where routes[i] is a bus route that the ith bus repeats forever.
>
>For example, if routes[0] = [1, 5, 7], this means that the 0th bus travels in the sequence 1 -> 5 -> 7 -> 1 -> 5 -> 7 -> 1 -> ... forever.
>You will start at the bus stop source (You are not on any bus initially), and you want to go to the bus stop target. You can travel between bus stops by buses only.
>
>Return the least number of buses you must take to travel from source to target. Return -1 if it is not possible.


- Example :

      Input: routes = [[1,2,7],[3,6,7]], source = 1, target = 6
      Output: 2
      Explanation: The best strategy is take the first bus to the bus stop 7, then take the second bus to the bus stop 6.
