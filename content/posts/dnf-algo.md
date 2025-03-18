+++
title = "The Dutch National Flag Algorithm: Efficient Sorting in Three Categories"
description = ""
type = ["posts","post"]
tags = [
    "Dutch National Flag Algorithm",
    "DSA",
    "Algorithm",
    "Backend",
]
date = "2025-01-05"
categories = [
    "Data Structures",
    "Algorithms",
]
series = ["Jyotsna 101"]
[ author ]
  name = "Jyotsna"
+++

![](https://miro.medium.com/v2/resize:fit:700/1*ZzXl4hi33T6jDpngN1OqBA.png)

The Dutch National Flag algorithm is a popular and efficient sorting technique for problems where elements can be divided into three distinct categories. Named after the Dutch national flag, where there are three horizontal stripes of different colors, this algorithm elegantly sorts an array of items into three groups with minimal swaps and comparisons.

In this blog post, we will explore the Dutch National Flag algorithm in detail, including how it works, its applications, and its benefits.

## What is the Dutch National Flag Algorithm?

The Dutch National Flag problem was introduced by Edsger W. Dijkstra in 1976. The problem asks to sort an array of elements where each element is one of three distinct categories (usually represented as 0, 1, and 2).

The algorithm is most commonly used to sort an array containing three different types of values, such as:

- **0** (Red)
- **1** (White)
- **2** (Blue)

For example, the problem might look like this: You are given an array of integers containing only `0`, `1`, and `2`, and you need to sort the array such that all `0`s come first, followed by `1`s, and `2`s last.

## How Does the Dutch National Flag Algorithm Work?

The Dutch National Flag algorithm uses a **three-way partitioning** strategy. It works by maintaining three pointers:

- **Low**: Points to the position where the next `0` should be placed.
- **Mid**: Points to the current element being considered.
- **High**: Points to the position where the next `2` should be placed.

Here’s how the algorithm operates:

1.  Start with `Low` at the beginning, `Mid` at the start of the array, and `High` at the end of the array.
2.  Traverse the array from `Mid` to `High`:

- If the current element is `0`, swap it with the element at `Low` and increment both `Low` and `Mid`.
- If the current element is `1`, just move `Mid` forward.
- If the current element is `2`, swap it with the element at `High` and decrement `High`.

This partitioning process ensures that, at the end, all `0`s are in the left section, `1`s are in the middle section, and `2`s are in the right section.

## Visualization

Let’s visualize the process with an example.

**Example Input**:

[2, 0, 1, 2, 1, 0]

- Initially:  
  `Low = 0, Mid = 0, High = 5 Array = [2, 0, 1, 2, 1, 0]`

**First iteration** (`Mid = 0`, `array[Mid] = 2`):

- Swap `array[Mid]` with `array[High]`.
- After the swap:
- `Array = [0, 0, 1, 2, 1, 2]`
- Decrement `High` to 4.

**Second iteration** (`Mid = 0`, `array[Mid] = 0`):

- Swap `array[Mid]` with `array[Low]`.
- After the swap:
- `Array = [0, 0, 1, 2, 1, 2]`
- Increment both `Low` and `Mid` to 1.

**Third iteration** (`Mid = 1`, `array[Mid] = 0`):

- Swap `array[Mid]` with `array[Low]` (already in place).
- Increment `Low` and `Mid` to 2.

**Fourth iteration** (`Mid = 2`, `array[Mid] = 1`):

- No swap required, just increment `Mid` to 3.

**Fifth iteration** (`Mid = 3`, `array[Mid] = 2`):

- Swap `array[Mid]` with `array[High]`.
- After the swap
- `Array = [0, 0, 1, 1, 2, 2]`
- Decrement `High` to 3.

At this point, `Mid` is greater than `High`, so the algorithm terminates.

**Final Sorted Array**:

[0, 0, 1, 1, 2, 2]

## Time Complexity

The Dutch National Flag algorithm runs in **O(n)** time complexity, where `n` is the number of elements in the array. This is because:

- Each element is processed exactly once.
- The algorithm uses a constant amount of space, making its space complexity **O(1)**.

## When Should You Use the Dutch National Flag Algorithm?

The Dutch National Flag algorithm is particularly useful when you are sorting an array that only contains three distinct values. Here are some typical use cases:

1.  **Sorting colors**: This is the original problem, where you have an array of colors (e.g., red, white, and blue) and need to sort them.
2.  **Partitioning arrays**: This can be used for problems like segregating even and odd numbers, or partitioning numbers into different categories based on conditions.
3.  **Three-way comparison**: Any problem that requires partitioning into three categories can benefit from this efficient algorithm.

## Code Example in Java

Here’s the Java code implementing the Dutch National Flag algorithm:

    public class DutchNationalFlag {
        public static void sortColors(int[] nums) {
            int low = 0, mid = 0, high = nums.length - 1;
            while (mid <= high) {
                if (nums[mid] == 0) {
                    // Swap nums[low] and nums[mid]
                    int temp = nums[low];
                    nums[low] = nums[mid];
                    nums[mid] = temp;
                    low++;
                    mid++;
                } else if (nums[mid] == 1) {
                    mid++;
                } else {
                    // Swap nums[mid] and nums[high]
                    int temp = nums[mid];
                    nums[mid] = nums[high];
                    nums[high] = temp;
                    high--;
                }
            }
        }
    public static void main(String[] args) {
            int[] nums = {2, 0, 1, 2, 1, 0};
            sortColors(nums);
            System.out.println(Arrays.toString(nums));
        }
    }

## Example

![](https://miro.medium.com/v2/resize:fit:513/1*4UeQPLUD5TN1VE2nEZN_rQ.jpeg)

## Conclusion

The Dutch National Flag algorithm is a powerful, efficient way to sort arrays with three distinct values. By maintaining three pointers, it sorts the array in a single pass, making it much faster than traditional sorting algorithms when dealing with limited categories.

Its linear time complexity and constant space complexity make it a great choice for problems where you need to partition arrays into three groups. Whether you’re sorting colors, separating even and odd numbers, or solving other partitioning problems, this algorithm provides an elegant solution.

### Further Reading

- [Edsger W. Dijkstra’s original paper](https://www.cs.utexas.edu/~EWD/ewd02xx/EWD214.PDF)
- [Algorithm visualizations](https://www.geeksforgeeks.org/dutch-national-flag-problem/)

If you have any questions about the Dutch National Flag algorithm or how to apply it to other problems, feel free to leave a comment below! Happy coding!
