class Solution {
    public String convert(String s, int numRows) {
        if(numRows == 1) return s;//行数为1时，直接输出原字符串
        String[] arr = new String[numRows];//定义一个一维字符串数组把结果按行储存
        Arrays.fill(arr,"");//将arr字符串中的每个值设为""
        char[] chars = s.toCharArray();//将原字符串转换为字符数组
        int len = chars.length;//得到源字符串的长度,也可用s.length();
        int period = numRows * 2 - 2;//定义指针，找到储存规律，存储周期为(2 * numRows - 2)
        for(int i = 0; i < len; i++){//遍历字符串（字符数组）
            int mod = i % period;//保证周期变化，使每个数在[0,period),为period个数及字符串数组中字符串的个数
            if(mod < numRows){//若所得数小于行数，则顺序存入
                arr[mod] += chars[i];//将指向的字符存入相应的字符串数组中
            }else{//若大于等于行数，则倒序存入
                arr[period - mod] += String.valueOf(chars[i]);//将字符数组中的字符转为字符串存入数组
            }
        }
        StringBuilder res = new StringBuilder();//定义res的StringBuilder字符串
        for(String ch : arr){//遍历字符串数组中的每个字符串
            res.append(ch);//将字符串连入res字符串
        }
        return res.toString();//将res原字符串输出
    }
}

![image](https://github.com/Algorithm-qiu/LeetCode/blob/Algorithm-qiu-patch-image/079FC822-91F0-4c20-A0C3-F4EF5BDB32A2.png)
