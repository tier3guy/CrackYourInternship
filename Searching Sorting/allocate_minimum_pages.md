[Question Link](https://practice.geeksforgeeks.org/problems/allocate-minimum-number-of-pages0937/1)

```
class Solution
{
        bool isvalid(int a[],int n,int k,int mx)
        {
            int stud=1, sm=0;
            for(int i=0;i<n;i++){
                sm+=a[i];

                if(sm>mx){
                    stud++;
                    sm=a[i];
                }
                if(stud>k) return false;
            }
            return true;
        }

    public:

    int findPages(int A[], int N, int M)
    {
        int start = A[0], end = 0;

        for(int i=0; i<N; i++){
            start = max(start, A[i]); // one must get alteast one book, hence
            end += A[i];
        }

        int mid, result = -1;
        while(start <= end){ // O(log n)

            mid = start + (end - start)/2;
            if(isvalid(A, N, M, mid)){ // O(n)
                result = mid;
                end = mid - 1;
            }
            else{
                start = mid + 1;
            }
        }

        // nlogn
        return result;
    }

};
```
