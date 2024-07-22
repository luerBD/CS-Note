# 1.数据结构

## 1.1 数组

### 1.1.1 数组中重复的数字

- 题目描述

  ```
  在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。
  数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。
  请找出数组中任意一个重复的数字。
  ```

- 测试用例

  - 一般是考虑功能用例，特殊（边缘）用例或者是反例，无效测试用例这三种情况。甚至可以从测试用例寻找一些规律解决问题，同时也可以让我们的程序更加完整鲁棒。
    - 功能用例：长度为n的数组中，包含1个或者多个重复的数字
    - 反例：数组中不包含重复的数字
    - 无效用例：输入数组为空或者包含0到n-1以外的数字

- 分析

  - 首先注意是确定是否全部找出还是随意一个、时间空间效率问题。

    - 问题确定：任意找出一个
    - 时间空间效率问题
      - 如果时间优先，可以使用辅助数组或者其他数据结构解决。
      - 如果空间优先，则只能在原数组上进行操作（同时也要考虑是否允许更改原数组，即是否可以进行排序或者调整位置）

  - 下面是几种解法思路以及时间空间复杂度比较：

    - 法1：暴力解法

      ```
      算法过程：最直接最简单的方式，直接使用双重循环，外层与内层循环数字比较，遇到重复数组直接返回该数字。
      是否改变原数组：否
      时间空间复杂度：O(n^2),O(1)
      ```

    - 法2：利用快速排序

      ```
      算法过程：对原数组进行快排，然后循环遍历比较相邻元素是否相同，相同直接返回该数字。
      是否改变原数组：是
      时间空间复杂度：O(nlogn),O(1) 
      ```

    - 法3：利用哈希表

      ```
      算法过程：遍历数组，将元素作为key，判断哈希表是否存在该key，如果存在则直接返回该元素；否则是第一次出现，其value初始化为1，存到哈希表中。
      优化：由于数组元素范围固定0~n-1，所以可以利用数组达到哈希表的作用。元素作为数组下标，判断其值是否大于1，大于直接返回，否则其值+1。
      
      是否改变原数组：否
      时间空间复杂度：O(n),O(n)
      ```

    - 法4：利用数字特点

      ```
      算法过程：从头到尾依次扫描这个数组中的每个数字。当扫描到下标为i的数字时，首先比较这个数字(用m表示)是不是等于i。
      如果是，则接着扫描下一个数字；
      如果不是，则再拿它和第m个数字进行比较。
      	如果它和第m个数字相等，就找到了一个重复的数字（该数字再下标为i和m的位置都出现了）；
      	如果它和第m个数字不等，就把第i个数字和第m个数字交换，把m放到属于它的位置。
      	接下来重复这个比较、交换的过程，直达我们发现一个重复的数字。
      	
      是否改变原数组：是
      时间空间复杂度：O(n),O(1)
      注意：代码中尽管有一个两重循环，但每个数字最多只要交换两次就能找到属于它自己的位置，因此总的时间复杂度是O(n)。
      另外，所有的操作步骤都是在输入数组上进行的，不需要额外分配内存，因此空间复杂度是O(1)
      ```

- 代码

  ```
  import java.util.Arrays;
  
  public class FindRepeatNumberInArray {
  
      // 解法1：暴力求解
      public static int findRepeatNumber1(int[] nums) {
          boolean result = illegalJudgment(nums);
          if (result == false) return -1;
          for (int i = 0; i < nums.length; i++) {
              for (int j = i + 1; j < nums.length; j++) {
                  if (nums[i] == nums[j]) {
                      return nums[i];
                  }
              }
          }
          return -1;
      }
  
      // 解法2：快排
      public static int findRepeatNumber2(int[] nums) {
          boolean result = illegalJudgment(nums);
          if (result == false) return -1;
          Arrays.sort(nums);
          for (int i = 0; i < nums.length - 1; i++) {
              if (nums[i] == nums[i + 1]) {
                  return nums[i];
              }
          }
          return -1;
      }
  
      // 解法3：哈希表
      public static int findRepeatNumber3(int[] nums) {
          boolean result = illegalJudgment(nums);
          if (result == false) return -1;
          HashMap<Integer, Integer> hashMap = new HashMap<>();
          for (int i = 0; i < nums.length; i++) {
              if(hashMap.containsKey(nums[i])){
                  return nums[i];
              }
              hashMap.put(nums[i], 0);
          }
          return -1;
      }
  
      // 解法4：数字特点，比较交换
      public static int findRepeatNumber4(int[] nums) {
          boolean result = illegalJudgment(nums);
          if (result == false) return -1;
          for (int i = 0; i < nums.length; i++) {
              while (nums[i] != i) {
                  if (nums[nums[i]] == nums[i]) {
                      return nums[i];
                  }
                  int temp = nums[i];
                  nums[i] = nums[temp];
                  nums[temp] = temp;
              }
          }
          return -1;
      }
  	
  	// 无效数据判断
      public static boolean illegalJudgment(int[] nums) {
          // 空指针以及没有元素
          if (nums == null && nums.length <= 0) {
              return false;
          }
          // 数组元素不在 0 到 n-1 范围内
          for (int i = 0; i < nums.length; i++) {
              if (nums[i] < 0 && nums[i] > nums.length - 1) {
                  return false;
              }
          }
          return true;
      }
  
      public static void main(String[] args) {
          int[] nums = {1, 2, 4, 3, 2, 1, 5, 6};
          System.out.println(findRepeatNumber1(nums));
          System.out.println(findRepeatNumber2(nums));
          System.out.println(findRepeatNumber3(nums));
          System.out.println(findRepeatNumber4(nums));
      }
  }
  
  
  ```

  


### 1.1.2 二维数组中的查找

- 题目描述

  ```
  在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。
  请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。
  ```

- 测试用例

  - 一般是考虑功能用例，特殊（边缘）用例或者是反例，无效测试用例这三种情况。甚至可以从测试用例寻找一些规律解决问题，同时也可以让我们的程序更加完整鲁棒。
    - 功能用例：待查找数字在二维数组中（包括最大值最小值）
    - 反例：待查找数字不在二维数组中（在最大最小之间，不在最大最小之间）
    - 无效用例：数组是null，或者没有元素

- 分析

  - 下面是几种解法思路以及时间空间复杂度比较。

    - 法1：暴力查找

      ```
      该方法不考虑题目的排序条件，直接遍历二维数组，找到返回true，否则返回false。
      时间空间复杂度O(m*n),O(1) 
      ```

    - 法2：线性查找

      ```
      该方法和二分查找有点类似（通过排除一部分元素达到快速找到的目的）。
      
      二分查找是取中间元素进行比较，然后判断目标值在左边还是右边。
      
      该题目虽然不能直接利用二分思想对二维数组进行处理，但是思想是一样的，可以逐行逐列进行排除。
      
      如：利用二维数组排序特点，选取右上角的元素作比较，（1）如果相等直接返回，（2）如果目标值小与该值，则可以排除最右边一列，（3）否则排除最上面一行。通过这种方法可以不断缩小查找区域，最终解决问题。选取左下角元素比较同理。
      
      具体过程：
      若数组为空，返回 false
      初始化行下标为 0，列下标为二维数组的列数减 1
      重复下列步骤，直到行下标或列下标超出边界
      获得当前下标位置的元素 num
      如果 num 和 target 相等，返回 true
      如果 num 大于 target，列下标减 1
      如果 num 小于 target，行下标加 1
      循环体执行完毕仍未找到元素等于 target ，说明不存在这样的元素，返回 false。
      
      时间空间复杂度O (m + n),O(1)
      ```

- 代码

  ```java
  public class FindNumberIn2DArray {
  	// 解法1：暴力查找（比较简单不再赘述）
  
  	// 解法2：线性查找
      public static boolean findNumberIn2DArray(int[][] matrix, int target) {
          // 无效输入
          if (matrix == null || matrix.length == 0 || matrix[0].length == 0) {
              return false;
          }
          // 特殊情况处理（小与最小值、大于最大值，直接返回）
          if (matrix[0][0] > target || matrix[matrix.length - 1][matrix[0].length - 1] < target) {
              return false;
          }
          int row = 0;
          int column = matrix[0].length - 1;
          while (row < matrix.length && column >= 0) {
              if (matrix[row][column] == target) {
                  return true;
              } else if (matrix[row][column] > target) {
                  column--;
              } else {
                  row++;
              }
          }
          return false;
      }
  
      public static void main(String[] args) {
          int[][] m = {{1, 4, 7, 11, 15},
                  {2, 5, 8, 12, 19},
                  {3, 6, 9, 16, 22},
                  {10, 13, 14, 17, 24},
                  {18, 21, 23, 26, 30}
          };
          System.out.println(findNumberIn2DArray(m, 5));
          System.out.println(findNumberIn2DArray(m, 50));
      }
  }
  ```

  

## 1.2 字符串

### 1.2.1 替换空格

- 题目描述

  ```
  实现一个函数，把字符串中的每个空格都替换成“%20”。
  ```

- 测试用例

  ```
  一般是考虑功能用例，特殊（边缘）用例或者是反例，无效测试用例这三种情况。甚至可以从测试用例寻找一些规律解决问题，同时也可以让我们的程序更加完整鲁棒。
  （1）功能用例：字符串有一个或者多个空格
  （2）反例：字符串没有空格，或字符串长度为0
  （3）无效用例：数组是null
  ```

  

- 分析：由于在Java中字符串String类型是不可变类型，所以没办法像C++一样在原来的字符串上进行修改，因此必须要开一个新的空间进行处理。下面是几种解法思路以及时间空间复杂度比较。

  - 解法1：利用Java字符串工具库（不建议）

    ```
    `s.replace(" ","%20")`，该方法直接满足题意要求，比较简单。
    ```

  - 解法2：遍历字符串，逐个进行替换

    ```
    首先遍历字符串记录空格数，然后计算总共需要的空间大小，创建字符数组，并重新遍历字符串，遇到空格替换，否则原字符存入。
    时间空间复杂度：O(n),O(n)
    ```

  - 解法3：遍历字符串，利用StringBuilder

    ```
    和解法2类似，只是使用StringBuild进行存储，不需要提前计算字符数组空间。遍历字符串，遇到空格则把%20添加，否则添加原字符。
    
    时间空间复杂度：O(n),O(n)
    ```

- 代码：

  ```
  public class ReplaceSpaceInString {
  	//解法2
      public static String replaceSpaceInString(String s){
          if (s == null || s.length() == 0) {
              return s;
          }
          int spaceCount = 0;
          char[] str = new char[32];
          int i = 0;
          while(i < s.length()){
              str[i] = s.charAt(i);
              if(s.charAt(i) == ' '){
                  spaceCount++;
              }
              i++;
          }
          int srcLength = s.length();
          int destLength = s.length() + spaceCount * 2;
  
          int p1 = srcLength, p2 = destLength;
          while(p1 >= 0 && p2 > p1){
              if(str[p1] == ' '){
                  str[p2--] = '0';
                  str[p2--] = '2';
                  str[p2--] = '%';
              }else{
                  str[p2--] = str[p1];
              }
              p1--;
          }
  
          return String.valueOf(str, 0, destLength);
      }
  
  	//解法3
      public static String replaceSpaceInString2(String s) {
          if (s == null || s.length() == 0) {
              return s;
          }
  
          StringBuilder sb = new StringBuilder();
          for(int i = 0; i < s.length(); i++){
              char c = s.charAt(i);
              if(c == ' '){
                  sb.append("%20");
              }else{
                  sb.append(c);
              }
          }
  
          return String.valueOf(sb);
      }
      public static void main(String[] args) {
          String s = "We are happy.";
          System.out.println(replaceSpaceInString(s));
          System.out.println(replaceSpaceInString2(s));
      }
  }
  
  ```

  





```cpp
#include <iostream>
using namespace std;

void ReplaceBlank(char str[], int length)
{
	if (str == nullptr || length <= 0) 
	{
		return;
	}
	int originalLength = 0;
	int blankNumber = 0;
	int i = 0;
	while (str[i] != '\0')
	{
		if (str[i] == ' ')
		{
			blankNumber++;
		}
		originalLength++;
		i++;
	}
	int newLength = originalLength + blankNumber * 2;
	if (newLength > length) 
	{
		return;
	}
	int originalIndex = originalLength;
	int newIndex = newLength;
	while (originalIndex >= 0 && newIndex > originalIndex)
	{
		if (str[originalIndex] == ' ')
		{
			str[newIndex--] = '0';
			str[newIndex--] = '2';
			str[newIndex--] = '%';
		}
		else 
		{
			str[newIndex--] = str[originalIndex];
		}
		originalIndex--;
	}
}
```

## 1.3 链表

### 1.3.1 从尾到头打印链表

- 题目描述

  ```
  输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。
  要求不能更改链表的结构
  ```

- 测试用例

  ```
  一般是考虑功能用例，特殊（边缘）用例或者是反例，无效测试用例这三种情况。甚至可以从测试用例寻找一些规律解决问题，同时也可以让我们的程序更加完整鲁棒。
  （1）功能用例：链表有多个节点
  （2）反例：链表只有一个节点
  （3）无效用例：链表为空
  ```

- 思路

  - 分析：

    由于需要整型数组作为返回值，所以遍历的时候结果要保存下来，因为不知道节点有多少，所以先用list保存，最后再存到整型数组。

  - 下面是几种解法思路以及时间空间复杂度比较。

    - 解法1：递归实现

      ```
      递归实现，其过程是从头节点开始递归，直到最后一个节点，然后每层返回时把节点值存到list里面，最后存到整型数组。
      时间空间复杂度：O(n),O(n)
      ```

    - 解法2：非递归，利用辅助栈

      ```
      非递归实现，遍历整个链表，将节点存到辅助栈，最后将栈元素弹到整型数组。
      时间空间复杂度：O(n),O(n)
      ```

- 代码

  ```java
  public class ListNode {
      public int val;
      public ListNode next;
  
      public ListNode(int val) {
          this.val = val;
          this.next = null;
      }
  
      @Override
      public String toString() {
          StringBuilder ret = new StringBuilder();
          for (ListNode cur = this; ; cur = cur.next) {
              if (cur == null) {
                  break;
              }
              ret.append(cur.val);
              ret.append("\t");
          }
          return ret.toString();
      }
  }
  import java.util.ArrayList;
  import java.util.List;
  import java.util.Stack;
  
  public class PrintReverseLink {
      // 解法1：递归实现
      public static int[] printReversingly1(ListNode head) {
          if (head == null) {
              return new int[0];
          }
          List<Integer> list = new ArrayList<>();
          printReversinglyCore1(head, list);
          int length = list.size();
          int[] result = new int[length];
          for (int i = 0; i < length; i++) {
              result[i] = list.get(i);
          }
          return result;
      }
  
      public static void printReversinglyCore1(ListNode node, List<Integer> list) {
          if (node == null) {
              return;
          }
          printReversinglyCore1(node.next, list);
          list.add(node.val);
      }
  
      // 解法2：非递归，使用辅助栈
      public static int[] printReversingly2(ListNode head) {
          if (head == null) {
              return new int[0];
          }
          ListNode node = head;
          Stack<Integer> stack = new Stack<>();
          while (node != null) {
              stack.add(node.val);
              node = node.next;
          }
          int length = stack.size();
          int[] result = new int[length];
          for (int i = 0; i < length; i++) {
              result[i] = stack.pop();
          }
          return result;
      }
  
      public static void main(String[] args) {
          ListNode head = new ListNode(1);
          head.next = new ListNode(2);
          head.next.next = new ListNode(3);
          System.out.println(head);
          int[] result1 = printReversingly1(head);
          for (int i = 0; i < result1.length; i++) {
              System.out.print(result1[i] + "\t");
          }
          System.out.println();
          int[] result2 = printReversingly2(head);
          for (int i = 0; i < result2.length; i++) {
              System.out.print(result2[i] + "\t");
          }
          System.out.println();
      }
  }
  
  ```

  

## 1.4 二叉树

### 1.4.1 重建二叉树

- 题目描述

  ```
  输入某二叉树的前序遍历和中序遍历的结果，请构建该二叉树并返回其根节点。
  假设输入的前序遍历和中序遍历的结果中都不含重复的数字。
  例如：先序遍历为[3,9,20,15,7]，中序遍历为 [9,3,15,20,7]，其对应的二叉树如下
  		  3
  	    /   \
  	  9 	20
             /  \
           15    7
  ```

- 测试用例

  ```
  一般是考虑功能用例，特殊（边缘）用例或者是反例，无效测试用例这三种情况。甚至可以从测试用例寻找一些规律解决问题，同时也可以让我们的程序更加完整鲁棒。
  （1）功能用例：完全与非完全二叉树。
  （2）边缘用例：只有一个节点，只有左节点，只有右节点。
  （3）无效用例：树为空，对应数组为空。
  ```

- 思路

  - 分析

    - 从数据结构中可知，根据二叉树的先序与中序遍历结果可以唯一的重建二叉树（另外根据后序与中序也可以唯一的重建二叉树）。需要注意的是：前提条件是，树中的任意两个节点值不能相同


    - 重建二叉树，最直接的想法是找到根节点，以及左右子树的节点集合，然后对每个节点不断递归即可。下面考虑如何找到根节点以及左右子树节点集合，并以上例举例（先序遍历为[3,9,20,15,7]，中序遍历为 [9,3,15,20,7]）。


    - 根节点：根据先序遍历的特点，第一个节点即是根节点（值为3的节点为根节点）。
    - 左右子树集合：根据中序遍历特点，根节点左边的节点集合为左子树（[ 9 ]），根节点右边的节点集合为右子树（[15,20,7]）

  - 下面是递归解法思路与具体过程、以及时间空间复杂度比较。

    - 解法：递归实现
      - 递归终止条件：当输入先序、中序遍历结果数组没有元素时，说明左/右子树构建完成，直接返回null即可。
      - 划分左右子树：根据先序遍历的第一个节点，找到中序遍历与之相同的节点，左边是左子树，右边是右子树
      - 构建根节点：根据先序遍历的第一个节点构建新节点，即当前根节点root
      - 递归构建左右子树：更新先序、中序遍历结果数组递归调用。
      - 返回值：最后回溯返回的根节点即整个二叉树的根节点。
      - 注意： 比较简单直接地方式是每次递归左右子树时，可以新建左右子树数组传进去进行处理，但会浪费时间与空间，优化方式是使用下标以及左右子树节点数量来代替，具体细节见代码。
      - 时间空间复杂度：O(n),O(n)

  - 难点：递归调用时候确定左右子树的开始位置与长度。

- 代码

  ```java
  class Solution {
      public TreeNode deduceTree(int[] preorder, int[] inorder) {
          if(preorder == null || 
             inorder == null || 
             preorder.length == 0 || 
             inorder.length == 0 || 
             preorder.length != 
             inorder.length){
              return null;
          }
          return deduceTreeCore(preorder, 0, inorder, 0, preorder.length);
      }
      public TreeNode deduceTreeCore(int[] preorder, int preStart, int[] inorder, int inStart, int length){
          if(length == 0){
              return null;
          }
          int index = -1;
          for(int i = inStart; i < inStart + length; i++){
              if(inorder[i] == preorder[preStart]){
                  index = i;
                  break;
              }
          }
          int leftLength = index - inStart;
          int rightLength = length - leftLength - 1;
          TreeNode root = new TreeNode(preorder[preStart]);
          
          root.left = deduceTreeCore(preorder, preStart + 1, inorder, inStart, leftLength);
          root.right = deduceTreeCore(preorder, preStart + leftLength + 1, inorder, index + 1, rightLength);
          return root;
      }
  }
  ```


### 1.4.2 二叉树的下一个节点

- 题目描述

  ```
  给定二叉树和其中一个节点（唯一参数），找到中序遍历序列的下一个节点。树中的节点除了有左右孩子指针，还有一个指向父节点的指针。
  ```

- 思路

  <img src="assets/image-20240711175819623.png" alt="image-20240711175819623" style="zoom:33%;" />

  

- 代码

  ```
  public class TreeNodeWithParent {
      public int val;
      public TreeNodeWithParent left;
      public TreeNodeWithParent right;
      public TreeNodeWithParent father;
  
      public TreeNodeWithParent(int val) {
          this.val = val;
          this.left = null;
          this.right = null;
          this.father = null;
      }
  }
  
  ```

  ```
  public class NextNodeInBinaryTrees {
      public static TreeNodeWithParent getNext(TreeNodeWithParent node) {
          if (node == null) {
              return null;
          }
  
          // 当前节点有右孩子
          if (node.right != null) {
              TreeNodeWithParent next_node = node.right;
              while (next_node.left != null) {
                  next_node = next_node.left;
              }
              return next_node;
          }
  
          // 没有右孩子，分为几种情况
          while (true) {
              // 没有父节点
              if (node.father == null) {
                  return null;
              }
              // 当前节点是父节点的左节点
              if (node.father.left == node) {
                  return node.father;
              }
              // 当前节点是父节点的右节点
              if (node.father.right == node) {
                  node = node.father;
              }
          }
      }
  
      public static void main(String[] args) {
          TreeNodeWithParent root = new TreeNodeWithParent(1);
  
          root.left = new TreeNodeWithParent(2);
          root.left.father = root;
  
          root.right = new TreeNodeWithParent(3);
          root.right.father = root;
  
          root.left.left = new TreeNodeWithParent(4);
          root.left.left.father = root.left;
  
          root.left.right = new TreeNodeWithParent(5);
          root.left.right.father = root.left;
  
          root.right.left = new TreeNodeWithParent(6);
          root.right.left.father = root.right;
  
          root.right.right = new TreeNodeWithParent(7);
          root.right.right.father = root.right;
  
          root.left.right.left = new TreeNodeWithParent(8);
          root.left.right.left.father = root.left.right;
  
          root.left.right.right = new TreeNodeWithParent(9);
          root.left.right.right.father = root.left.right;
  
          System.out.println(root.left.val + "->" + getNext(root.left).val); // 2->8
  
          System.out.println(root.val + "->" + getNext(root).val); // 1->6
  
          System.out.println(root.left.right.right.val + "->" + getNext(root.left.right.right).val); // 9->1
  
          System.out.println(root.right.right.val + "->" + getNext(root.right.right)); // 7->nullW
      }
  }
  
  ```

  

## 1.5 栈和队列

### 1.5.1 用两个栈实现队列

- 题目描述
  - 用两个栈，实现队列的从队尾插入元素offer()和从队头抛出元素poll()。
  - ***leetcode链接：** [用两个栈实现队列](https://leetcode-cn.com/problems/yong-liang-ge-zhan-shi-xian-dui-lie-lcof/)（以下代码已测试，提交通过）*
- 思路
  - 将元素依次压入栈1；
  - 将栈1中的每个元素依次出栈并依次压入栈2；
  - 将栈2中的每个元素依次出栈；

- 代码

  ```
  import java.util.Stack;
  
  public class MyQueue {
      private Stack<Integer> stack1 = new Stack<>();
      private Stack<Integer> stack2 = new Stack<>();
  
      public void offer(Integer data) {
          stack1.push(data);
      }
  
      public Integer poll() {
          if (!stack2.isEmpty()) {
              return stack2.pop();
          } else {
              if (!stack1.isEmpty()) {
                  while (!stack1.isEmpty()) {
                      Integer data = stack1.pop();
                      stack2.push(data);
                  }
                  return stack2.pop();
              } else {
                  return null;
              }
          }
      }
  
      public static void main(String[] args) {
          MyQueue myQueue = new MyQueue();
          System.out.println(myQueue.poll());
          myQueue.offer(1);
          myQueue.offer(2);
          myQueue.offer(3);
          System.out.println(myQueue.poll());
          System.out.println(myQueue.poll());
          myQueue.offer(4);
          System.out.println(myQueue.poll());
          System.out.println(myQueue.poll());
          System.out.println(myQueue.poll());
      }
  }
  
  ```

  

# 2.算法和数据操作

## 2.1 递归和循环

### 2.1.1 斐波那契数列

***leetcode链接：** [斐波那契数列](https://leetcode-cn.com/problems/fei-bo-na-qi-shu-lie-lcof/)（以下代码已测试，提交通过）*

- 题目描述

  ```
  写一个函数，输入 n ，求斐波那契（Fibonacci）数列的第 n 项（即 F(N)）。斐波那契数列的定义如下：
      F(0) = 0,   F(1) = 1
      F(N) = F(N - 1) + F(N - 2), 其中 N > 1.
  斐波那契数列由 0 和 1 开始，之后的斐波那契数就是由之前的两数相加而得出。
  ```

- 思路
  - 递归：会出现大量重复计算，效率不好（如计算f(6)与f(7)时，最后都会重复计算f(6)、f(5)等），因此可以把计算的中间项保存下来，避免重复计算；
  - 循环：可以使用循环实现，从下往上计算，因此需要两个临时变量记录前面计算过的结果。

- 代码：

  ```
  public class Fibonacci {
      // 递归解法，由于重复计算导致效率低，复杂度为O(n^2)
      public static int fibonacciRecursionly(int n) {
          if (n < 0) {
              return -1;
          }
          if (n == 0 || n == 1) {
              return n;
          } else {
              return (fibonacciRecursionly(n - 1) + fibonacciRecursionly(n - 2)) % 1000000007;
          }
      }
  
      // 循环解法，从下往上计算，避免重复计算，复杂度为O(n)
      public static int fibonacciCyclely(int n) {
          int fibonacci = 0;
          if (n < 0) {
              return -1;
          }
          if (n == 0 || n == 1) {
              return n;
          } else {
              int n_2 = 0;
              int n_1 = 1;
              for (int i = 2; i <= n; i++) {
                  int temp = n_2 % 1000000007;
                  n_2 = n_1 % 1000000007;
                  n_1 = (temp + n_1) % 1000000007;
              }
              fibonacci = n_1;
          }
          return fibonacci;
      }
  
      public static void main(String[] args) {
          System.out.println("递归实现");
          System.out.println(fibonacciRecursionly(13));
  
          System.out.println("循环实现");
          System.out.println(fibonacciCyclely(13));
      }
  }
  ```


## 2.2 查找和排序

### 2.2.1 旋转数组的最小数字

***leetcode链接：** [旋转数组的最小数字](https://leetcode-cn.com/problems/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof/)（以下代码已测试，提交通过）*

- 题目描述

  ```
  把一个数组最开始的若干个元素搬到末尾成为数组的旋转，如
      1,2,3,4,5=>3,4,5,1,2；
      0,1,1,1,1=>1,1,1,0,1；
      0,1,1,1,1=>1,0,1,1,1。
  求一个原本递增的数组旋转后的最小数字。
  ```

- 思路
  - 
