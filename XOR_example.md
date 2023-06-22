Cho một dãy số nguyên trong đó có 1 số không có cặp. Tìm số đó

Vd : 2 3 2 1 1 => 3

Dùng xor

1^1 = 0

0^0 = 0

Cách giải

int ans =0;

for(int i=0;i<nums.size();i++)

    ans=ans^nums[i];
    
return ans;

ans : 00

2   : 10

ans : 10

3   : 11

ans : 01

2   : 10

ans : 11

1   : 01

ans : 10

1   : 01

ans : 11

=> 3
