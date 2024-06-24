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

  

- 解法1：修改数组

  ```c
  #include<stdio.h>
  int duplicate(int numbers[], int length, int* duplication)
  {
  	int i;
  	if (numbers == NULL || length <= 0)
  	{
  		return 0;
  	}
  	for (i = 0; i < length; ++i)
  	{
  		if (numbers[i] < 0 || numbers[i] > length - 1)
  		{
  			return 0;
  		}
  	}
  	for (i = 0; i < length; ++i)
  	{
  		while (numbers[i] != i)
  		{
  			if (numbers[i] != numbers[numbers[i]])
  			{
  				*duplication = numbers[i];
  				return 1;
  			}
  			int temp = numbers[i];
  			numbers[i] = numbers[numbers[i]];
  			numbers[numbers[i]] = temp;
  		}
  	}
  	return 0;
  }
  ```

- 解法2：不修改数组

  ```c++
  #include <iostream>
  using namespace std;
  int countRange(const int* numbers, int length, int start, int end)
  {
  	int count = 0;
  	if (numbers == NULL || length <= 0)
  	{
  		return 0;
  	}
  	for (int i = 0; i < length; i++)
  	{
  		if (numbers[i] >= start && numbers[i] <= end)
  		{
  			count++;
  		}
  	}
  	return count;
  }
  int getDuplication(const int* numbers, int length) 
  {
  	if (numbers == NULL || length <= 0) 
  	{
  		return -1;
  	}
  	int start = 1, end = length - 1;
  	while (start <= end) 
  	{
  		int middle = ((end - start) >> 1) + start;
  		int count = countRange(numbers, length, start, middle);
  		if (start == end) 
  		{
  			if (count > 1) 
  			{
  				return start;
  			}
  			else 
  			{
  				break;
  			}
  		}
  		if (count > middle - start + 1)
  		{
  			end = middle;
  		}
  		else 
  		{
  			start = middle + 1;
  		}
  	}
  	return -1;
  }
  
  ```


### 1.1.2 二维数组中的查找

```cpp
#include <iostream>
using namespace std;
bool Find(int matrix[][4], int rows, int columns, int number)
{
	bool found = false;
	if (matrix != nullptr && rows > 0 && columns > 0) 
	{
		int row = 0;
		int column = columns - 1;
		while (row < rows && column >= 0) 
		{
			if (matrix[row][column] == number)
			{
				found = true;
				break;
			}
			else if (matrix[row][column] > number)
			{
				--column;
			}
			else 
			{
				++row;
			}
		}
	}
	return found;
}

int main() 
{
	int matrix[][4] = 
	{
		{1, 2, 8, 9},
		{2, 4, 9, 12},
		{4, 7, 10, 13},
		{6, 8, 11, 15}
	};
	int rows = sizeof(matrix) / sizeof(matrix[0]);
	int column = sizeof(matrix[0]) / sizeof(matrix[0][0]);
	cout << Find(matrix, rows, column, 7) << endl;
	return 0;
}
```

## 1.2 字符串

### 1.2.1 替换空格

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

```cpp
struct ListNode 
{
	int data;
	ListNode* next;
};

void PrintList(ListNode* L) 
{
	stack<ListNode*> nodes;
	ListNode* p = L;
	while (p != nullptr) 
	{
		nodes.push(p);
		p = p->next;
	}
	while (!nodes.empty()) 
	{
		cout << nodes.top()->data << " ";
		nodes.pop();
	}
	cout << endl;
}
```

## 1.4 二叉树

### 1.4.1 重建二叉树

```c
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */

 struct TreeNode* deduceTreeCore(int* startPreorder, int* endPreorder, int* startInorder, int* endInorder)
{
    // 在先序遍历序列中找到根节点的值
    int rootValue = startPreorder[0];
    struct TreeNode* root = (struct TreeNode *)malloc(sizeof(struct TreeNode));
    root->val = rootValue;
    root->left = root->right = NULL;

    // 在中序遍历序列中找到根节点的值
    int* rootInorder = startInorder;
    while(rootInorder <= endInorder && *rootInorder != rootValue)
    {
        rootInorder++;
    }

    int leftLength = rootInorder - startInorder;        // 获取中序序列中左子树节点个数
    int* leftPreorderEnd = startPreorder + leftLength;  // 指向先序序列中左子树的末尾结点

    // 如果中序序列中左子树节点个数>0的话，就可以创建左子树了
    if(leftLength > 0)
    {
        root->left = deduceTreeCore(startPreorder + 1, leftPreorderEnd, startInorder, rootInorder - 1);
    } 

    // 如果中序序列中左子树节点个数 == 除根节点以外的节点个数的话，说明该树是一棵左单支树，没有右子树，此时就不用创建右子树了
    // 否则就可以创建右子树
    if(leftLength < endPreorder - startPreorder)
    {
        root->right = deduceTreeCore(leftPreorderEnd + 1, endPreorder, rootInorder + 1, endInorder);
    }
    return root;


}
struct TreeNode* deduceTree(int* preorder, int preorderSize, int* inorder, int inorderSize) 
{
    if(preorder == NULL || inorder == NULL || preorderSize == 0 || inorderSize == 0)
    {
        return NULL;
    }
    return deduceTreeCore(preorder, preorder + preorderSize - 1, inorder, inorder + inorderSize - 1);
}

```

