```
#include "bits/stdc++.h"
using namespace std;

int minimumCost(vector<int> arr){

  int n = arr.size();
  int mid;
  if(n % 2){
    mid = arr[n / 2];
  }
  else{
    mid = (arr[n / 2] + arr[(n - 2) / 2]) / 2;
  }

  int cost = 0;
  for(auto num : arr){
    cost += abs(num - mid);
  }

  return cost;
}

int main(){

  vector<int> arr = {1, 100, 101};
  cout << minimumCost(arr) << "\n";

  return 0;
}
```
