# Leetcode-1780

# C++

class Solution {
public:
    bool checkPowersOfThree(int n) {
        vector<long long>v(16,1);
        for(int i=1;i<16;i++)
        {
            v[i]=v[i-1]*3;
        }
        map<int,int>mp;
        while(n)
        {
            for(int i=0;i<16;i++)
            {
                if(v[i]>n)
                {
                    n-=v[i-1];
                    if(mp[v[i-1]])return false;
                    mp[v[i-1]]=1;
                    break;
                }
            }
        }
        return true;
    }
};

# Java

import java.util.HashMap;

class Solution {
    public boolean checkPowersOfThree(int n) {
        int[] v = new int[16];
        v[0] = 1;

        // Fill the array with powers of 3
        for (int i = 1; i < 16; i++) {
            v[i] = v[i - 1] * 3;
        }

        HashMap<Integer, Integer> map = new HashMap<>();

        while (n > 0) {
            for (int i = 0; i < 16; i++) {
                if (v[i] > n) {
                    n -= v[i - 1];
                    if (map.containsKey(v[i - 1])) {
                        return false;
                    }
                    map.put(v[i - 1], 1);
                    break;
                }
            }
        }

        return true;
    }
}

# Python

class Solution:
    def checkPowersOfThree(self, n: int) -> bool:
        v = [1] * 16
        for i in range(1, 16):
            v[i] = v[i - 1] * 3  # Generate powers of 3
        
        mp = {}  # Dictionary to track used powers of 3
        
        while n:
            for i in range(16):
                if v[i] > n:
                    n -= v[i - 1]
                    if v[i - 1] in mp:
                        return False
                    mp[v[i - 1]] = 1
                    break
        
        return True
