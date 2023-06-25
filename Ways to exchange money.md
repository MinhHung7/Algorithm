# Problem: Cho một số tiền N, tính số cách đổi số tiền đó với các mệnh giá. Biết các mệnh giá gồm : 1000, 2000, 5000, 10000, 20000, 50000, 100000, 200000, 500000
## Test mẫu :
- N = 7000. Có 6 cách đổi
- 1000 1000 1000 1000 1000 1000 1000
- 1000 1000 1000 1000 1000 2000
- 1000 1000 1000 2000 2000
- 1000 2000 2000 2000
- 1000 1000 5000
- 2000 5000
## Thay vì ta xét 1000, 2000, ... thì mình sẽ xét 1, 2 ,... cho đơn giản
## Nhận xét :
- Ta thấy các cách như {2000 5000} và {5000 2000} là một => Ta nên xét các cách {x<sub>1</sub> x<sub>2</sub> ...} trong đó x<sub>1</sub> <= x<sub>2</sub>
- Như các cách ở trên thì N có thể được tạo thành từ các dãy x<sub>1</sub> x<sub>2</sub> ... và ta phân biệt chúng bằng mệnh giá cuối cùng x<sub>n</sub>
- Ta gọi `dp[sum][mark]` là số cách đổi tạo thành số tiền là `sum` trong đó mệnh giá `mark` là mệnh giá cuối cùng
- Vd: 1 1 2 5 => `dp[9][5]`
- Ta thấy răng để duyệt tới tập {1 1 2 5} hay dp[9][5] ta cần duyệt tới tập dp[9 - 5][x<sub>o</sub>] hay dp[4][x<sub>o</sub>] với x<sub>o</sub> là mệnh giá cuối cùng trong sum = 4.
- Lúc này dp[9][5] = dp[4][1] + dp[4][2]. x<sub>o</sub> = {1, 2}.
- Như đã nói ở trên
  - Ta cần xét x<sub>1</sub> <= x<sub>2</sub>
  - Thêm vào đó không tồn tại dp[i][j] với j > i
  - Từ 2 điều trên suy ra: Từ dp[i][j] = dp[i-j][x<sub>o</sub>] + dp[i-j][x<sub>1</sub>] + ... Với x<sub>i</sub> <= min (i-j, j)
  ### Tới đây là đủ để quy hoạch động, giờ ta tìm các trường hợp cơ bản
  - `dp[i][i] = 0` với i là các mệnh giá. Vd dp[10][10] = 1. Chỉ cần 1 tờ cũng thỏa điều kiện.
  ### Code
  ```cpp
  #include <bits/stdc++.h>
  using namespace std;
  int dp[800][500];  // Lưu các cách đổi số tiền (Có thể đổi từ 800k thành các mệnh giá <= 500k
  int a[] = {1, 2, 5, 10, 20, 50, 100, 200, 500};  // Các mệnh giá
  int main()
  {
  	int n;
  	cin >> n;

    // Để tìm được các cách đổi tờ tiền N ta cần tìm số cách đổi từ 1 -> n
  	for (int i = 1; i <= n; ++i) 
  	{
  		for (int j = 0; j < 9; ++j)
  		{ Tìm xem có thể đổi được tờ nào không
  			if (a[j] < i)
  			{
  				for (int k = 0; k < 9; ++k)
  				{ // Ta tìm cách phân hoạch thành tiền nhỏ hơn
  					if (a[k] <= min(a[j], i - a[j]))  // Không thể có chuyện dp[10][20]
  					{
              // Vd: dp[8][2] = dp[6][1] + dp[6][2].
  						dp[i][a[j]] += dp[i - a[j]][a[k]];
  					}
  				}
  			}
  			if (a[j] == i)
  			{
          // Trường hợp cơ bản dp[5][5] = 1
  				dp[i][a[j]] = 1;
  			}
  		}
  	}
    // Ta thấy các cách đổi N = 8 
    // Là dp[8][1] + dp[8][2] + dp[8][5]
  	int ans = 0;
  	for (int i = 0; i < 9; ++i)
  	{
  		if (a[i] <= n)
  			ans += dp[n][a[i]];
  	}
  	cout << ans;
  	return 0;
  }
  ```
