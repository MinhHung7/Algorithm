# Problem: Cho một mảng chứa n phần tử. Tìm các phần tử không xuất hiện trong mảng trong khoảng [1..n]
## Khảo sát: Cho một mảng a[8] = [4, 3, 2, 7, 8, 2, 3, 1]. Ta thấy trong khoảng [1..8] thiếu số {5, 6}
- Với 4: đưa a[4 - 1] = a[3] = 7 về -7 => a[3] = -7 => a[8] = [4, 3, 2, -7, 8, 2, 3, 1]
- Với 3: đưa a[3 - 1] = a[2] = 2 về -2 => a[2] = -2 => a[8] = [4, 3, -2, -7, 8, 2, 3, 1]
- Với -2: đưa a[2 - 1] = a[1] = 3 về -3 => a[1] = -3 => a[8] = [4, -3, -2, -7, 8, 2, 3, 1]
- Với -7: đưa a[7 - 1] = a[6] = 3 về -3 => a[6] = -3 => a[8] = [4, -3, -2, -7, 8, 2, -3, 1]
- Với 8: đưa a[8 - 1] = a[7] = 1 về -1 => a[7] = -1 => a[8] = [4, -3, -2, -7, 8, 2, -3, -1]
- Với -2: đưa a[2 - 1] = a[1] = -3 về -3 => a[1] = -3 => a[8] = [4, -3, -2, -7, 8, 2, -3, -1]
- Với -3: đưa a[3 - 1] = a[2] = -2 về -2 => a[2] = -2 => a[8] = [4, -3, -2, -7, 8, 2, -3, -1]
- Với -1: đưa a[1 - 1] = a[0] = 4 về -4 => a[0] = -4 => a[8] = [-4, -3, -2, -7, 8, 2, -3, -1]
- Duyệt từ [0..n-1] nếu a[i] > 0 thì i+1 là số bị thiếu => 5, 6
### Mã code
```cpp
vector<int> findDisappearedNumbers(vector<int>& nums) {
        vector<int>ans;
        for(int i=0;i<nums.size();++i){
            if(nums[i]>0 && nums[nums[i]-1] > 0){
                nums[nums[i]-1] = - nums[nums[i]-1];
            }
            else if(nums[i]<0 && nums[-nums[i]-1] > 0){
                nums[-nums[i]-1] = - nums[-nums[i]-1];
            }
        }
        for(int i=0;i<nums.size();++i){
            if(nums[i]>0){
                ans.push_back(i+1);
            }
        }
        return ans;
    }
```
