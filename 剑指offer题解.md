## 1.数组中重复的数字

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


## 2.二维数组中的查找

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

