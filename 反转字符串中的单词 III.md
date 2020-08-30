给定一个字符串，你需要反转字符串中每个单词的字符顺序，同时仍保留空格和单词的初始顺序。

 

示例：

输入："Let's take LeetCode contest"
输出："s'teL ekat edoCteeL tsetnoc"

```
  public String reverseWords(String s) {
        String res = "";
        String tp  = "";
        for(int i =0;i<s.length();i++){
            if(s.charAt(i) == ' '){
               res  = res + tp + " " ;
               tp  = "";
            }
            else { 
               tp = s.charAt(i) + tp;
            }
        }
        res += tp;
        return res;
    }
```