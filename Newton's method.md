# Problem: tính xấp xỉ nghiệm của một phương trình f(x)
## Vd: - Tính xấp xỉ sqrt(n) => f(x) = x^2 - n;
##     - Tính nghiệm xấp xỉ x^3-2x^2+5x-4 = 0;
## Phương pháp: Nghiệm cần tìm x_(n+1) = x_n - f(x_n)/f'(x_n)
Vd: tính xấp xỉ sqrt(n)
```cpp
int mySqrt(int n) {
        if(n==0) return 0;
        if(n==1) return 1;
        
        // f(x) = x^2-n
        // f'(x) = 2x
        double xo = (double) n;
        double x1 = xo - (xo*xo-n)/(2*xo);
        while(abs(x1-xo) >= 1){
            xo = x1;
            x1 = xo - (xo*xo-n)/(2*xo);
        }
        return (int)x1;
    }
```
