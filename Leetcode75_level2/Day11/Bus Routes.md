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

- ## Solution:
```cpp
class Solution {
public:
    bool MapIntersection(map<int, bool>& m1, map<int, bool>& m2) {
        for(const auto&[key, val]: m1) {
            if (m2.find(key) != m2.end()) return true;
        }
        return false;
    }
    void UpdateGraph(map<int, vector<int>>& graph, int a1, int a2) {
        auto mapIt = graph.find(a1);
        if (mapIt == graph.end()) {
            graph[a1] = {a2};
        } else {
            mapIt->second.push_back(a2);
        }
    }
    bool PresentInTargetNodes(vector<int>& nodes, int s) {
        for(auto v: nodes) {
            if (v==s) return true;
        }
        return false;
    }
    bool VecIntersectionIsNotEmpty(vector<int>& v1, vector<int>& v2) {
        for(auto s1: v1) {
            if (PresentInTargetNodes(v2, s1)) return true;
        }
        return false;
    }
    int numBusesToDestination(vector<vector<int>>& routes, int source, int target) {
        if (source == target) return 0;
        map<int, map<int, bool>> routesMap;
        vector<int> sourceRoutes, targetRoutes;
        for(int i=0; i<routes.size(); i++) {
            map<int, bool> oneRoute;
            for(auto s: routes[i]) {
                if (s==source) sourceRoutes.push_back(i);
                if (s==target) targetRoutes.push_back(i);
                oneRoute[s] = true;
            }
            routesMap[i] = oneRoute;
        }
        if (VecIntersectionIsNotEmpty(sourceRoutes, targetRoutes)) return 1;
        map<int, vector<int>> graph;
        for(int i=0; i<routes.size(); i++) {
            for(int j=i+1; j<routes.size(); j++) {
                if (MapIntersection(routesMap[i], routesMap[j])) {
                    UpdateGraph(graph, i, j);
                    UpdateGraph(graph, j, i);
                }
            }
        }
        std::deque<int> curNodes;
        for(auto s: sourceRoutes) curNodes.push_back(s);
        map<int, bool> visited;
        int ans = 0;
        while(!curNodes.empty()) {
            std::deque<int> nextCurNodes;
            ans++;
            for(auto s: curNodes) {
                auto childNodes = graph[s];
                visited[s] = true;
                for(auto c: childNodes) {
                    if (visited[c]) continue;
                    if (PresentInTargetNodes(targetRoutes, c)) return ans+1;
                    nextCurNodes.push_back(c);
                }
            }
            curNodes.clear();
            curNodes = nextCurNodes;
        }
        return -1;
    }
};
```
