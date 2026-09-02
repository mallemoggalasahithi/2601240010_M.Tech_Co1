# Divide and Conquer

## 1. Large Student Dataset

You have **1 crore (10 million) student records** and need to sort them efficiently.

### Question

How can the **Divide-and-Conquer strategy** be applied? Identify the **divide, conquer, and combine** steps.

### Solution

According to the scenario, the **Merge Sort** algorithm can be used to sort **1 crore student records efficiently**.

Merge Sort follows the **Divide-and-Conquer** strategy by:

* **Divide:** Dividing the large dataset into smaller halves.
* **Conquer:** Sorting each smaller half recursively.
* **Combine:** Merging the sorted halves to obtain the final sorted dataset.

### Merge Sort Applies the Divide-and-Conquer

Merge Sort is suitable for a very large dataset because it repeatedly divides the data into smaller parts and sorts them efficiently.

### Example

Imagine a college has a large dataset containing student marks, and the marks need to be sorted in **ascending order**.

**Student Marks:**

38, 27, 43, 3, 9, 82, 10, 25

Suppose we want to sort these marks in ascending order.

---

### 1. Divide

The first step is to **divide the dataset into two halves**.

**Original Dataset:**

38, 27, 43, 3, 9, 82, 10, 25

**First Division:**

**Left Half:**

38, 27, 43, 3

**Right Half:**

9, 82, 10, 25

Again divide each half:

**Left Half:**

38, 27

**Right Half:**

43, 3

**Left Half:**

9, 82

**Right Half:**

10, 25

Continue dividing until each part contains only one element:

38 | 27 | 43 | 3 | 9 | 82 | 10 | 25

---

### 2. Conquer

Now, each smaller part is **sorted recursively**.

Compare the elements and arrange them in ascending order.

**38, 27**

→ 27, 38

**43, 3**

→ 3, 43

**9, 82**

→ 9, 82

**10, 25**

→ 10, 25

Now we have:

27, 38 | 3, 43 | 9, 82 | 10, 25

---

### 3. Combine

The sorted smaller parts are now **merged together**.

First merge:

27, 38 + 3, 43

→ **3, 27, 38, 43**

Second merge:

9, 82 + 10, 25

→ **9, 10, 25, 82**

Finally, merge the two sorted parts:

3, 27, 38, 43 + 9, 10, 25, 82

→ **3, 9, 10, 25, 27, 38, 43, 82**

Therefore, the final sorted student marks are:

**3, 9, 10, 25, 27, 38, 43, 82**

# Algorithm

### Input

* Student records array `arr`
* Number of student records `n`

### Steps

1. Start with the given student records.
2. Check if the array contains one or zero elements.
3. If yes, return the array because it is already sorted.
4. Find the middle position of the array.
5. Divide the array into two halves.
6. Recursively sort the left half.
7. Recursively sort the right half.
8. Merge the two sorted halves.
9. Continue until all student records are sorted.
10. Return the final sorted array.

# Python Implementation

```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr

    mid = len(arr) // 2

    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])

    return merge(left, right)


def merge(left, right):
    result = []
    i = 0
    j = 0

    while i < len(left) and j < len(right):

        if left[i] <= right[j]:
            result.append(left[i])
            i += 1

        else:
            result.append(right[j])
            j += 1

    result.extend(left[i:])
    result.extend(right[j:])

    return result


# Student records
student_marks = [38, 27, 43, 3, 9, 82, 10, 25]

# Sort the student records
sorted_marks = merge_sort(student_marks)

print("Sorted student marks:", sorted_marks)
```

# Output


Sorted student marks: [3, 9, 10, 25, 27, 38, 43, 82]
```

# Time Complexity

### Worst Case

**O(n log n)**

### Best Case

**O(n log n)**



**O(n)**

