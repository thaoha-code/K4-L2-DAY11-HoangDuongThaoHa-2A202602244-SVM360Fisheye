# So sánh L với R

Chỉ số L/R là thứ tự box cao ≥ H=40 trong từng frame, theo thứ tự XML; bắt đầu từ 1.
Box L trong ignore_region được báo IGNORE_SCOPE, không tính SPURIOUS.

## adasind_145860.jpg
- L3 mid IGNORE_SCOPE
## adasind_167700.jpg
- L9 mid IGNORE_SCOPE
- L10 mid IGNORE_SCOPE
- L3 mid SPURIOUS
- L11+R4 center WRONG_CLASS
- R2 mid MISSING
## adasind_199770.jpg
- L7 mid IGNORE_SCOPE
- L9 edge IGNORE_SCOPE
- L8+R2 edge ATTRIBUTE
- L5 center SPURIOUS
- L6 edge SPURIOUS
- R3 mid MISSING
- R4 mid MISSING
- R5 edge MISSING
- R6 edge MISSING

## Theo zone
| zone | n_ref | matched | missing | spurious |
|---|---|---|---|---|
| center | 9 | 8 | 1 | 2 |
| mid | 7 | 4 | 3 | 1 |
| edge | 4 | 2 | 2 | 1 |
