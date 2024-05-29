# 1.数据结构

## 面试题3.数组中重复的数字

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


## 面试题4.二维数组中的查找

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

## 面试题5.替换空格

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

## 面试题6.从尾到头打印链表

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

## 面试题7.重建二叉树

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

