[Question Link](https://practice.geeksforgeeks.org/problems/find-pair-given-difference1559/1)

```
bool findPair(int arr[], int size, int n){
    sort(arr, arr + size);

    int i = 0, j = 1;
    while(i < size && j < size){
        if(abs(arr[i] - arr[j]) == n && i != j) return true;
        else if(abs(arr[i] - arr[j]) > n) i++;
        else j++;
    }

    return false;
}
```
