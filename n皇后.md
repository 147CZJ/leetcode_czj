n 皇后问题研究的是如何将 n 个皇后放置在 n×n 的棋盘上，并且使皇后彼此之间不能相互攻击。



上图为 8 皇后问题的一种解法。

给定一个整数 n，返回所有不同的 n 皇后问题的解决方案。

每一种解法包含一个明确的 n 皇后问题的棋子放置方案，该方案中 'Q' 和 '.' 分别代表了皇后和空位

```
 public List<List<String>> solveNQueens(int n) {
         List<List<String>> res = new ArrayList<>();
        char[][] tp = new char[n][n];
        for(int i =0;i<n;i++){
            for(int j =0;j<n;j++){
                tp[i][j] = '.';
            }
        }

        board(0, n , tp, res);
        return res;
    }
    public void board(int i, int n , char[][] tp  , List<List<String>> res){
        if(i == n ){
            ArrayList<String> re = new ArrayList<>();
            for(int m = 0;m<n;m++){
                String s = "";
                for(int p =0; p<n;p++){
                    s+=tp[m][p];
                }
                re.add(s);
            }
            res.add(re);
            return ;
        }
        for(int q =0;q<n;q++){
            if(check(tp, i, q, n)){
                tp[i][q] = 'Q';
                board(i+1, n,tp, res);
                tp[i][q] = '.';
            }
        }
    }
    public boolean  check(char[][]tp, int i , int j , int n ){
        for(int m =0;m<n; m++ ){
            if(tp[i][m] == 'Q') return false;
            if(tp[m][j] == 'Q') return false;
        }
        int x = i;
        int y = j;
        while(x>=0&&y>=0){
            if(tp[x][y] == 'Q') return false;  
            x--;
            y--;
        }
        while(i>=0&&j<n){
            if(tp[i][j] == 'Q') return false;
            i--;
            j++;
        }
        return true;
    }
```