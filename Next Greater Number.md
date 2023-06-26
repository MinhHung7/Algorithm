# Problem: Cho một mảng số nguyên, tìm số lớn hơn gần nhất đối với mỗi phần tử trong mảng, nếu không có thì mặc định là -1
## Ví dụ: a = [5, 3, 2, 10, 6, 8, 1, 4, 12, 7, 4]
=> **Answer = [10, 10, 10, 12, 8, 12, 4, 12, -1, -1, -1]**
## Hướng giải: Dùng Stack
![](https://github.com/MinhHung7/Algorithm/blob/main/Next%20Greater%20Element.jpg)

## Code
```cpp
class Solution {
public:
    vector<int> nextGreaterElement(vector<int>& nums1, vector<int>& nums2) {
        vector<int>ans;
        map<int, int>mp;
        stack<int>st;
        for(int i=0;i<nums2.size();++i){
            while(st.size() && st.top() < nums2[i]){
                mp[st.top()] = nums2[i];
                st.pop();
            }
            st.push(nums2[i]);
        }
        for(int i=0;i<nums1.size();++i){
            ans.push_back(mp[nums1[i]]==0?-1:mp[nums1[i]]);
        }
        return ans;
    }
};
```
