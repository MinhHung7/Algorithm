# Problem: Tính TÍCH 2 số LỚN 
## Hướng đi:
$$
\begin{align*}
1456754 \\
\times 23456776543 \\
\end{align*}
$$

Gọi n là số chữ số của các số

Vd: 1456754 => n = 7
## Dùng chia để trị
1456754 = 1456 * $10^{n/2}$ + 754 = 1456 * $10^3$ + 754

=> x = a * $10^{n/2}$ + b

=> y = c * $10^{n/2}$ + d

=> x * y = (a * $10^{n/2}$ + b) * (c * $10^{n/2}$ + d)

&#8195;&#8195;&#8195;&#8195;= ac * $10^n$ + (ad + bc) * $10^{n/2}$ + bd

### Ta thấy
&#8195;&#8195;&#8195; ac = karatsuba(a, c)

&#8195;&#8195;&#8195; bd = karatsuba(b, d)

&#8195;&#8195;&#8195; (ad + bc) = karatsuba(a + b, c + d) - ac - bd

&#8195;&#8195;&#8195; Giải thích: (a+b)*(c+d) = ad + bc + ac + bd
