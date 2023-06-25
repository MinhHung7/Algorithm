# Problem: Cho một chuỗi s, kiểm tra xem có thể tái xây dựng s chỉ bằng các substring của s hay không
## Ví dụ: 
- abab => true
- abba => false
## Hướng giải:
- Tạo chuỗi mới t bằng s + s
  - Vd: s = abcabc => t = abcabcabcabc
- Bỏ kí tự đầu và cuối của t
  - Vd: t = bcabcabcab
- Tìm trong chuỗi t mới có chuỗi s hay không. Nếu có trả về true. Còn không trả về false
## Code
```cpp
class Solution {
public:
    bool repeatedSubstringPattern(string s) {
        string t = s+s;
        t.pop_back();
        return (t.find(s, 1) >= 0 && t.find(s, 1) < t.size());
    }
};
```
