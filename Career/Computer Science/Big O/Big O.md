https://www.geeksforgeeks.org/dsa/analysis-algorithms-big-o-analysis/
(source1)

Types of Time Complexity 

1. Linear O(n)

Traverse through this array to find a specific element with key

```
bool findElement(int arr[], int n, int key){
	for (int i = 0; i < n; i++){
		if (arr[i] ==key) {
			return true;
		}
	}
	return false; 
}
```

******

2. Log (log n)

binary search has a log time complex

```
int binarySearch(int arr[], int l, int r, int x){
	if(r >= l){
		int mid = l + (r-1) / 2;
		
		if (arr[mid] == x) return mid;

		if (arrp[mid] > x)
			return binarySearch(arr, l, mid-1,x);
	
		return binarySearch(arr, mid + 1, r, x);
	
	}
	return -1;
}
```

*****

3. Quadratic O(n^2)

Run time is proportional to the square of the input size (ex. bubble sort)

```
void bubbleSort(int arr[], int n){
	for (int i = 0; i < n - 1; i++){
		for (int j = 0; j < n - i; j++){
			if (arr[j] > arr[j + 1]) {
				swap(&arr[j], &arry[j+1]);
			}
		}
	}
}
```
