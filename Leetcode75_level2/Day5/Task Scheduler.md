# Task Scheduler
- ## Question:
>Given a characters array tasks, representing the tasks a CPU needs to do, where each letter represents a different task. Tasks could be done in any order. Each task >is done in one unit of time. For each unit of time, the CPU could complete either one task or just be idle.
>
>However, there is a non-negative integer n that represents the cooldown period between two same tasks (the same letter in the array), that is that there must be at >least n units of time between any two same tasks.
>
>Return the least number of units of times that the CPU will take to finish all the given tasks.



- Example :

      Input: tasks = ["A","A","A","B","B","B"], n = 2
      Output: 8
      Explanation: 
      A -> B -> idle -> A -> B -> idle -> A -> B
      There is at least 2 units of time between any two same tasks.

- ## Solution:
```cpp
class Solution {
public:
    int leastInterval(vector<char> tasks, int n) {
        int freq[26];
        for(int i=0;i<26;i++) freq[i] = 0; 
        for(char task : tasks) ++freq[task-'A'];

        int time = 0;
        priority_queue<int> taskQue;
        for (int f : freq) if (f != 0) taskQue.push(f);
        queue<pair<int,int>> upcomingTask; // task & time
        while(!taskQue.empty() || !upcomingTask.empty()) {
            if (!upcomingTask.empty() && upcomingTask.front().second <= time) {
                taskQue.push(upcomingTask.front().first);
                upcomingTask.pop();
            }
            time +=1; // timer
            if(!taskQue.empty()) {
                int task = taskQue.top() - 1; taskQue.pop();
                if(task > 0) upcomingTask.push({task, time + n});
            }
        }
        return time;
    }
};
```
