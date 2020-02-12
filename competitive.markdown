### lessons from competitve programming 
- topic might not be same of simple manipulation

- need good intuition of count starting with 0 ,  /2 ends up.:
convert no of ele to count

- n numbers of elements; so count up to n-1;

- median : n-1/2 th if odd; n-1/2, ((n-1)/2)+1 if even

- if counts to skip, how many, from where, to where

- never try to optimize result from method of induction unless completed.
- for a and b, reordering : if one is max(a,b) then other is min(a,b).
- iterating in relfection : (without mid value) 
  [start + i] = ; i ranges (0 to length) 
  [end -i] = 
  length --; as we are doing two operations.
- iterating in reflection : (with midvalue) 
  [mid + i] = (val - i) ; i ranges (mid - start  to end - start) 
