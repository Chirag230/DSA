Given an integer array nums sorted in non-decreasing order, remove some duplicates in-place such that each unique element appears at most twice. The relative order of the elements should be kept the same.

class Solution {
public:
    int removeDuplicates(vector<int>& nums) 
    {
        int j =0;
        for(int i=0;i<nums.size();i++)
        {
            if(j==0 || j==1 || nums[j-2] != nums[i])
            {
                nums[j] = nums[i];
                j++;
            }
        }
    return j ;
    }
};