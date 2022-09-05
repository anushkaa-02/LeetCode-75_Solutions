# Course Schedule II
- ## Question:
>There are a total of numCourses courses you have to take, labeled from 0 to numCourses - 1. You are given an array prerequisites where prerequisites[i] = [ai, bi] >indicates that you must take course bi first if you want to take course ai.
>
>For example, the pair [0, 1], indicates that to take course 0 you have to first take course 1.
>Return the ordering of courses you should take to finish all courses. If there are many valid answers, return any of them. If it is impossible to finish all courses, >return an empty array.

- Example :

      Input: numCourses = 2, prerequisites = [[1,0]]
      Output: [0,1]
      Explanation: There are a total of 2 courses to take. To take course 1 you should have finished course 0. So the correct course order is [0,1].

- ## Solution:
```cpp
class Solution {
public:
	vector<int> findOrder(int n, vector<vector<int>>& arr) {

		vector<int> adj[n];
		int indeg[n];

		memset(indeg,0,sizeof(indeg));
		for(auto x:arr){
			adj[x[1]].push_back(x[0]);
			indeg[x[0]]++;   
		}

		queue<int> q;
		for(int i=0;i<n;i++){
			if(indeg[i]==0)
				q.push(i);
		}

		vector<int> ans;
		while(!q.empty())
		{
			int ele=q.front();
			q.pop();

			ans.push_back(ele);

			for(auto x:adj[ele]){
				indeg[x]--;
				if(indeg[x]==0)
					q.push(x);
			}
		}

		for(int i=0;i<n;i++){
			if(indeg[i]!=0)
				return {};
		}

		return ans;
	}

};
```
