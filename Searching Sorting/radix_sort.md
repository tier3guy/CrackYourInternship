Question : Code Radix Sort

Prerequisite : Counting Sort

[Learn Counting Sort](https://www.youtube.com/watch?v=pEJiGC-ObQE)
[Learn Radix Sort](https://www.youtube.com/watch?v=Il45xNUHGp0)

```
#include "bits/stdc++.h"
using namespace std;

int getMaxElement(vector<int> &array)
{
  int maximum = array[0];
  for (int i = 1; i <= array.size(); i++)
    maximum = max(maximum, array[i]);
  return maximum;
}

void countSort(vector<int> &array, int position, vector<int> &hash, vector<int> &backup)
{

  for (int i = 0; i < hash.size(); i++)
    hash[i] = 0;

  // count sort ka algorithm
  int digit;
  for (int i = 0; i < array.size(); i++)
  {

    digit = (array[i] % (position * 10)) / position;
    hash[digit] += 1;
  }

  for (int i = 1; i < hash.size(); i++)
  {

    hash[i] += hash[i - 1];
  }

  for (int i = array.size() - 1; i >= 0; i--)
  {

    digit = (array[i] % (position * 10)) / position;
    backup[--hash[digit]] = array[i];
  }

  for (int i = 0; i < backup.size(); i++)
    array[i] = backup[i];
}

void radixSort(vector<int> &array)
{

  if (array.size() == 0)
    return;

  vector<int> hash(10, 0);
  vector<int> backup(array.size(), 0);

  int max_element = getMaxElement(array);
  for (int position = 1; max_element / position > 0; position *= 10)
  {
    countSort(array, position, hash, backup);
  }
}

void display(vector<int> &vect)
{
  for (int i = 0; i < vect.size(); i++)
    cout << vect[i] << " ";
  cout << "\n";
}

int main(int argc, char **argv)
{

  vector<int> vect = {432, 8, 530, 90, 88, 231, 11, 45, 677, 199};

  cout << "Initial Array : ";
  display(vect);

  radixSort(vect);

  cout << "Sorted Array : ";
  display(vect);

  return 0;
}
```
