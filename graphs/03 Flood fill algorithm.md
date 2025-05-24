# Flood fill algorithm

An image is represented by a 2-D array of integers, each integer representing the pixel value of the image. Given a coordinate (sr, sc) representing the starting pixel (row and column) of the flood fill, and a pixel value newColor, "flood fill" the image.



To perform a flood fill, consider the starting pixel, plus any pixels connected 4-directionally to the starting pixel of the same colour as the starting pixel, plus any pixels connected 4-directionally to those pixels (also with the same colour as the starting pixel), and so on. Replace the colour of all of the aforementioned pixels with the newColor.

```cpp
class Solution{
    public:
    vector<vector<int>> floodFill(vector<vector<int>> &image,
                                  int sr, int sc, int newColor) {
      

      int prevColor  = image[sr][sc];

      if(prevColor == newColor) return image;
      vector<int> drow = {-1,0,1,0};
      vector<int> dcol = {0,1,0,-1};

      int n = image.size();
      int m = image[0].size();

      queue<pair<int,int>> q;
      q.push({sr,sc});
      image[sr][sc] = newColor;


      while(!q.empty()){
        int currRow = q.front().first;
        int currCol = q.front().second;
        q.pop();

        for(int d = 0; d < 4;d++){
            int nrow = currRow+drow[d];
            int ncol = currCol+dcol[d];

            if(nrow >= 0 && nrow < n && ncol >= 0 && ncol < m && image[nrow][ncol] == prevColor){
                q.push({nrow,ncol});
                image[nrow][ncol] = newColor;
            }
        }
      }

      return image;
    }
};
```