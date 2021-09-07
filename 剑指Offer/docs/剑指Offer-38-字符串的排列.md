# 剑指Offer-38-字符串的排列

## [题目链接](https://leetcode-cn.com/problems/zi-fu-chuan-de-pai-lie-lcof/)

## 解析

方法一：回溯



## 参考代码
```Java
    class Solution {
        List<String> list;
        StringBuilder tmp;
        boolean[] used;
        public String[] permutation(String s) {
            //全局变量初始化
            this.list = new ArrayList<String>();
            this.tmp = new StringBuilder();
            this.used = new boolean[s.length()];

            char[] arr = s.toCharArray();
            Arrays.sort(arr);
            backTrack(arr,0);
            return list.toArray(new String[0]);
        }

        public void backTrack(char[] arr,int index){
            if(index == arr.length){
                list.add(tmp.toString());
                return;
            }
            for(int i = 0; i < arr.length; i++){
                if(i > 0 && arr[i - 1] == arr[i] && !used[i - 1])  continue;
                if(!used[i]) {
                    tmp.append(arr[i]);
                    used[i] = true;
                    backTrack(arr,index + 1);
                    used[i] = false;
                    tmp.deleteCharAt(tmp.length() - 1);
                }
            }
        }
    }
```