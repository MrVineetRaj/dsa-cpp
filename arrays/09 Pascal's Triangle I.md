# Pascal's Triangle I

Given two integers r and c, return the value at the rth row and cth column (1-indexed) in a Pascal's Triangle.

In Pascal's triangle:

- The first row contains a single element 1.
- Each row has one more element than the previous row.
- Every row starts and ends with 1.

For all interior elements (i.e., not at the ends), the value at position (r, c) is computed as the sum of the two elements directly above it from the previous row:

- Pascal[r][c]=Pascal[r−1][c−1]+Pascal[r−1][c]
- where indexing is 1-based

```cpp
class Solution {

private:

  int calcNcR(int n, int r){
    int numIteration  = min(n-r,r);

    int result  = 1;

     /*
      Simulating
      10 * 9 * 8
      __________

      1 * 2 * 3
      */
    for(int i = 1; i <= numIteration;i++){
      result=((result)*(n-i+1))/i;
    }
    return result;
  }

public:
    int pascalTriangleI(int r, int c) {
      //reducing r and c by one as for ncr we need n-1 and r-1
      r--; // as n
      c--; // as r

      return calcNcR(r,c);
    }
};
```
