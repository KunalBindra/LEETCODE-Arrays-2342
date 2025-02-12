# LEETCODE-Arrays-2342
### **Understanding the Code**
1. **Method `gds(int num)`:**
   - Computes the sum of digits of `num`.

2. **Method `maximumSum(int[] nums)`:**
   - Iterates through the array `nums` and groups numbers based on their digit sum (computed using `gds`).
   - Uses a `HashMap<Integer, Integer>` (`map`) to store the maximum number encountered for each digit sum.
   - If a number with the same digit sum already exists, computes the possible pair sum and updates `result` accordingly.

---

### **Dry Run Example**
#### **Input:**
```java
nums = [51, 71, 17, 42]
```

#### **Step-by-Step Execution:**
| Iteration | `nums[i]` | `gds(nums[i])` | `map` Before | Condition Check | `result` Update | `map` After |
|-----------|----------|----------------|--------------|----------------|----------------|--------------|
| 1         | 51       | 5+1 = 6        | `{}`         | No existing key | No update      | `{6 → 51}`  |
| 2         | 71       | 7+1 = 8        | `{6 → 51}`   | No existing key | No update      | `{6 → 51, 8 → 71}` |
| 3         | 17       | 1+7 = 8        | `{6 → 51, 8 → 71}` | `map.containsKey(8)` | `result = max(-1, 17+71) = 88` | `{6 → 51, 8 → max(71, 17) = 71}` |
| 4         | 42       | 4+2 = 6        | `{6 → 51, 8 → 71}` | `map.containsKey(6)` | `result = max(88, 42+51) = 93` | `{6 → max(51, 42) = 51, 8 → 71}` |

#### **Final Output:**
```java
return 93;
```

---

### **Summary**
- The algorithm groups numbers based on their digit sum.
- It keeps track of the largest number encountered for each digit sum.
- If another number with the same digit sum appears, it computes the pair sum and updates the maximum found.
- **Time Complexity:** \(O(N)\), since we iterate over `nums` once.
- **Space Complexity:** \(O(N)\) in the worst case due to the HashMap.
