# 46. Permutations
Given a collection of **distinct** integers, return all possible permutations.

#### Example:
<pre>
<strong>Input:</strong> [1,2,3]
<strong>Output:</strong>
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
</pre>

## Solutions (Rust)

### 1. Backtracking
```Rust
impl Solution {
    pub fn permute(nums: Vec<i32>) -> Vec<Vec<i32>> {
        if nums.is_empty() {
            return vec![Vec::new()];
        }

        let mut ret = Vec::new();

        for i in 0..nums.len() {
            let mut nums_clone = nums.clone();
            nums_clone.remove(i);

            let mut back_ret = Self::permute(nums_clone);

            for arr in &mut back_ret {
                arr.push(nums[i]);
            }
            ret.append(&mut back_ret);
        }

        ret
    }
}
```
