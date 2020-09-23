<div align="center">

## Sorting and Searching Algorithms


</div>

### Description

This code contains all the common sorting/searching algorithms, all with comments. The program fills an array of user specified size with random numbers, then the program times the sorting and searching algorithms (picked at the user's discretion).
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Matt Fowler](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/matt-fowler.md)
**Level**          |Advanced
**User Rating**    |5.0 (20 globes from 4 users)
**Compatibility**  |C\+\+ \(general\), Borland C\+\+
**Category**       |[Algorithms](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/algorithms__3-29.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/matt-fowler-sorting-and-searching-algorithms__3-5269/archive/master.zip)

### API Declarations

```
#include <iostream.h>
#include <time.h>
#include <stdio.h>
#include <math.h>
```


### Source Code

```
#include <iostream.h>
#include <time.h>
#include <stdio.h>
#include <math.h>
/***************************************/
/* Sorting and Searching Algorighms  */
/*     By Matt Fowler       */
/* E-mail: philosopher150@yahoo.com  */
/*    Use this code freely     */
/***************************************/
void fillArray(int *a);
void resizeArray(int nSize, int *a);
int round(float toround);
/* sorting algorithms */
void QuickSort(int *a, int left, int right);
int Partition(int *a, int l, int r);
void MergeSort(int *a, int l, int r);
void merge(int *a, int l, int m, int r);
void ShellSort(int *a);
void SelectionSort(int *a);
void InsertionSort(int *a);
void BubbleSort(int *a);
/* searching algorithms */
/* All return index of element containing key */
/* Else return -1 */
int binary(int *a, int key);
int interpolate(int *a, int key);
int linear(int *a, int key);
int ternary(int *a, int key);
int ARR_MAX, passes;
int main()
{
int *arr, choice, foundAt, searchFor;
time_t start, end;
float dif;
cout<<"Common Searching/Sorting Algorithms"<<endl;
cout<<"By Matt Fowler"<<endl;
cout<<"E-mail: philosopher150@yahoo.com"<<endl;
cout<<endl;
cout<<"How many elements do you want in the array?: ";
cin>>ARR_MAX;
arr = new int[ARR_MAX];
cout<<"Program is now generating random elements from 0 to 1000."<<endl;
fillArray(arr);
cout<<"Done..."<<endl;
cout<<"Which sort do you want to use?"<<endl;
cout<<"1. Quicksort"<<endl;
cout<<"2. Merge Sort"<<endl;
cout<<"3. Shell Sort"<<endl;
cout<<"4. Selection Sort"<<endl;
cout<<"5. Insertion Sort"<<endl;
cout<<"6. Bubble Sort"<<endl;
cout<<endl;
cout<<"Enter Choice: ";
cin>>choice;
cout<<endl;
switch(choice)
{
  case 1:
  cout<<"Sorting..."<<endl;
  start = clock();
  QuickSort(arr, 0, ARR_MAX-1);
  end = clock();
  cout<<endl;
  cout<<"Sorted."<<endl;
  cout<<endl;
  dif = (end-start)/float(CLK_TCK)*1000;
  cout<<"Quick sort took "<<dif<<" milliseconds."<<endl;
  cout<<endl;
  break;
  case 2:
  cout<<"Sorting..."<<endl;
  start = clock();
  MergeSort(arr, 0, ARR_MAX-1);
  end = clock();
  cout<<endl;
  cout<<"Sorted."<<endl;
  cout<<endl;
  dif = (end-start)/float(CLK_TCK)*1000;
  cout<<"Merge sort took "<<dif<<" milliseconds."<<endl;
  cout<<endl;
  break;
  case 3:
  cout<<"Sorting..."<<endl;
  start = clock();
  ShellSort(arr);
  end = clock();
  cout<<endl;
  cout<<"Sorted."<<endl;
  cout<<endl;
  dif = (end-start)/float(CLK_TCK)*1000;
  cout<<"Shell sort took "<<dif<<" milliseconds."<<endl;
  cout<<endl;
  break;
  case 4:
  cout<<"Sorting..."<<endl;
  start = clock();
  SelectionSort(arr);
  end = clock();
  cout<<endl;
  cout<<"Sorted."<<endl;
  cout<<endl;
  dif = (end-start)/float(CLK_TCK)*1000;
  cout<<"Selection sort took "<<dif<<" milliseconds."<<endl;
  cout<<endl;
  break;
  case 5:
  cout<<"Sorting..."<<endl;
  start = clock();
  InsertionSort(arr);
  end = clock();
  cout<<endl;
  cout<<"Sorted."<<endl;
  cout<<endl;
  dif = (end-start)/float(CLK_TCK)*1000;
  cout<<"Insertion sort took "<<dif<<" milliseconds."<<endl;
  cout<<endl;
  break;
  case 6:
  cout<<"Sorting..."<<endl;
  start = clock();
  BubbleSort(arr);
  end = clock();
  cout<<endl;
  cout<<"Sorted."<<endl;
  cout<<endl;
  dif = (end-start)/float(CLK_TCK)*1000;
  cout<<"Bubble sort took "<<dif<<" milliseconds."<<endl;
  cout<<endl;
  break;
  default:
  cout<<"Enter a valid number, mofo!"<<endl;
  break;
}
cout<<"Select a searching algorithm:"<<endl;
cout<<"1. Ternary Search"<<endl;
cout<<"2. Binary Search"<<endl;
cout<<"3. Linear Interpolation"<<endl;
cout<<"4. Linear Search"<<endl;
cout<<endl;
cout<<"Enter a choice: ";
cin>>choice;
cout<<endl;
cout<<"Enter a number between 0-1000 to search for: ";
cin>>searchFor;
if((choice>1000) || (choice <0))
  cout<<"Enter a valid number!"<<endl;
cout<<endl;
switch(choice)
{
  case 1:
  cout<<"Searching..."<<endl;
  start = clock();
  foundAt = ternary(arr, searchFor);
  end = clock();
  cout<<endl;
  if(foundAt > -1)
   cout<<"Found at element "<<foundAt<<endl;
  else
   cout<<"Not found"<<endl;
  dif = (end-start)/float(CLK_TCK)*1000;
  cout<<endl;
  cout<<"Search took "<<dif<<" milliseconds"<<endl;
  cout<<endl;
  cout<<"Search took "<<passes<<" passes to find"<<endl;
  break;
  case 2:
  cout<<"Searching..."<<endl;
  start = clock();
  foundAt = binary(arr, searchFor);
  end = clock();
  cout<<endl;
  if(foundAt > -1)
   cout<<"Found at element "<<foundAt<<endl;
  else
   cout<<"Not found"<<endl;
  dif = (end-start)/float(CLK_TCK)*1000;
  cout<<endl;
  cout<<"Search took "<<dif<<" milliseconds"<<endl;
  cout<<endl;
  cout<<"Search took "<<passes<<" passes to find"<<endl;
  break;
  case 3:
  cout<<"Searching..."<<endl;
  start = clock();
  foundAt = interpolate(arr, searchFor);
  end = clock();
  cout<<endl;
  if(foundAt > -1)
   cout<<"Found at element "<<foundAt<<endl;
  else
   cout<<"Not found"<<endl;
  dif = (end-start)/float(CLK_TCK)*1000;
  cout<<endl;
  cout<<"Search took "<<dif<<" milliseconds"<<endl;
  cout<<endl;
  cout<<"Search took "<<passes<<" passes to find"<<endl;
  break;
  case 4:
  cout<<"Searching..."<<endl;
  start = clock();
  foundAt = linear(arr, searchFor);
  end = clock();
  cout<<endl;
  if(foundAt > -1)
   cout<<"Found at element "<<foundAt<<endl;
  else
   cout<<"Not found"<<endl;
  dif = (end-start)/float(CLK_TCK)*1000;
  cout<<endl;
  cout<<"Search took "<<dif<<" milliseconds"<<endl;
  cout<<endl;
  cout<<"Search took "<<foundAt<<" passes to find"<<endl;
  break;
  default:
  cout<<"Enter a valid choice, mofo!"<<endl;
  break;
}
delete []arr;
return 0;
}
/* fill the array with random data */
void fillArray(int *a)
{
  srand(time(NULL));
  for(int i = 0; i<ARR_MAX-1; i++)
   a[i] = rand()%1000;
}
/* Resize the array without losing data */
void resizeArray(int nSize, int *a)
{
  int i = 0;
  int *cpy = new int[nSize];
  for(; i<ARR_MAX; i++)
   cpy[i] = a[i];
  ARR_MAX = nSize;
  delete []a;
  a = new int[ARR_MAX];
  for(i = 0; i<ARR_MAX; i++)
   a[i] = cpy[i];
  delete []cpy;
}
/* Quick sort is the fastest sorting algorithm known.
  It works by finding a pivot (it can be any number)
  and then anything greater than the pivot goes to the
  right, and anything less goes to the left (partitioning). Then a new
  pivot is picked and the process is repeated until sorted.
  It has a run time efficency of about O(N log N)
  in the average case */
void QuickSort(int *a, int left, int right)
{
	int pivot_index;
	if (left < right)
	{
		pivot_index = Partition(a,left,right);
		QuickSort(a,left,pivot_index-1);
		QuickSort(a,pivot_index+1, right);
	}
}
int Partition(int *a, int l, int r)
{
  int i = l-1, j = r, z = a[r], temp;
  for(;;)
  {
   while(a[++i] < z);
   while(z < a[--j])
     if(j == l)
      break;
   if(i >= j)
     break;
    temp = a[i];
    a[i] = a[j];
    a[j] = temp;
  }
  temp = a[i];
  a[i] = a[r];
  a[r] = temp;
  return i;
}
/* Merge sort is a very efficent algorithm. It works by splitting
  the array into many parts (recursively), sorting those parts,
  and then joining them all back together (merging). This algorithm
  has a run time efficency of O(N log N). */
void MergeSort(int *a, int l, int r)
{
  if(r<=l)
   return;
  int m = (r+l)/2;
  MergeSort(a, l , m);
  MergeSort(a, m+1, r);
  merge(a, l, m, r);
}
void merge(int *a, int l, int m, int r)
{
  int i, j;
  static int *copy = new int[ARR_MAX];
  for(i = m+1; i > l; i--)
   copy[i-1] = a[i-1];
  for(j = m; j < r; j++)
   copy[r+m-j] = a[j+1];
  for(int k = l; k <= r; k++)
   if(copy[j] < copy[i])
     a[k] = copy[j--];
   else
     a[k] = copy[i++];
}
/* The problem with insertion sort is that it checks data elements
  that are right next to each other. This is what mainly slows
  down thw algorithm. Shell sort solves this. It uses an increment
  sequence to check elements of the array that are in different parts.
  Then preforms a standard insertion sort. The run time efficency
  of shellsort is unknown, but it is theorized to be along the lines
  of O(N(log N)^2). But no one is able to say for sure */
void ShellSort(int *a)
{
  int z, l = 0, r = ARR_MAX-1;
  /* set up increment sequence reccomended by Donald Knuth */
  /* 1 4 13 40 121 364 ... */
  for(z = 1; z <= (r+1)/9; z = 3*z+1);
   for(; z>0; z/=3)
     for(int i = l+z; i<=r; i++)
     {
      int j = i;
      int v = a[i];
      while(j>=l+z && v < a[j-z])
      {
        a[j] = a[j-z];
        j-=z;
      }
      a[j] = v;
     }
}
/* Selection sort works by finding the smallest number in the array
  and then swapping it with the number in the next position. It
  is very slow, and shouldn't be used with large lists. It has a
  run time efficency of O(N^2) */
void SelectionSort(int *a)
{
  int len = ARR_MAX-1;
  int cs, cp, temp, il;
  for(cp = 0; cp<=len; cp++)
  {
   cs = cp;
   for(il = cp; il<=len; il++)
   {
     if(a[il]<a[cs])
      cs = il;
   }
   temp = a[cp];
   a[cp] = a[cs];
   a[cs] = temp;
  }
}
/* Insertion sort works by finding parts of the array that are out
  of order and then moving them to their correct place. It is a slow
  algorithm, but is much faster than bubble or selection. It shouldn't
  be used on large sets of data. O(N^2) is its run time efficency */
void InsertionSort(int *a)
{
  int i, temp;
  for(i = ARR_MAX-1; i > 0; i--)
  {
   if(a[i]<a[i-1])
   {
    temp = a[i];
    a[i] = a[i-1];
    a[i-1] = temp;
   }
  }
  for(i = 2; i<=ARR_MAX-1; i++)
  {
   int j = i, v = a[i];
   while(v < a[j-1])
   {
     a[j] = a[j-1];
     j--;
   }
   a[j] = v;
  }
}
/* bubble sort swaps adjacent elements that are out of order
  and repeats the process until the whole list is ordered.
  Bubble sort shouldn't be used, its extremely slow.
  It has a run time efficency of O(N^2) */
void BubbleSort(int *a)
{
  int temp;
  for(int i = 0; i<=ARR_MAX-1; i++)
  {
   for(int j = 0; j<ARR_MAX-1; j++)
   {
     if(a[j]>a[j+1])
     {
      temp = a[j];
      a[j] = a[j+1];
      a[j+1] = temp;
     }
   }
  }
}
/* Search Algorithms. These will only work on SORTED data (exc linear) */
/* binary works by splitting the array in two. If the number in
  the middle is less than the key, it redividies up the right,
  then it continues the search in the same fashion.
  Otherwise, it redivides up the left. This is a fast algorithm
  and has a run time efficency of O(lg N) */
int binary(int *a, int key)
{
	int midval, left, right;
	left = 0;
	right = ARR_MAX-1;
	passes = 0;
	while(left<=right)
	{
	passes++;
  midval = (left+right)/2;
	if(a[midval] == key)
			return midval;
		else
			if(a[midval]<key)
				left = midval+1;
			else
				right = midval-1;
	}
	return -1;
}
/* Ternary has the same concept as binary, except instead of
  splitting the array in two parts, it splits it into three.
  Hence, it now checks two items instead of one, and then
  resplits the array based on analysis of those numbers.
  It has a run time efficency of O(log N) (log base 3) */
int ternary(int *a, int key)
{
	int left = 0, right = ARR_MAX-1, thirds, twothirds;
	passes = 0;
	while(left <= right)
	{
		passes++;
    thirds = left+(right-left)/3;
		twothirds = (thirds + right)/2;
		if(a[thirds]==key)
			return thirds;
		else if(a[thirds]<key)
			left = thirds + 1;
		else if(a[thirds]>key)
			right = thirds - 1;
		if(a[twothirds]== key)
			return twothirds;
		else if(a[twothirds]<key)
			left = twothirds + 1;
		else if(a[twothirds]>key)
			right = twothirds - 1;
	}
	return -1;
}
/* linear is the brute force approach. It starts from the begenning,
  checking every element of the array. Its the slowest search,
  however, its the only search that can be used on random data.
  But if you've ordered data, it dosen't make sense to use this.
  It has a runtime efficency of O(N) */
int linear(int *a, int key)
{
	int len = ARR_MAX+1;
	resizeArray(len, a);
	a[len-1] = key; /* insert key in the end, for efficency */
	int i = 0;
	while(a[i]!=key) /* with key in end while loop does less comparisions*/
		i++;     /* saving a bit of time */
	if(i == len-1)
		return -1;
	else
		return i;
}
/* Rounding. To solve some integer math problems in interpolation */
int round(float toround)
{
	int nondec = toround;
	float test = toround - nondec;
	if(test < .5)
		return floor(toround);
	else
		return ceil(toround);
}
/* Somewhat like a binary search, except instead of dividing
  the array in two, the function solves a proportion to determine
  where the data should be. Kinda like figuring out the data's
  equation. This is a VERY fast algorithm, but it can be clunky.
  If the data isn't randomly distributed things can get screwy,
  also, things can mess up if the key is near the end.
  Run time efficency is about O(log N) (but with a VERY small base) */
int interpolate(int *a, int key)
{
	float middle, tostart;
	int left = 0, right = ARR_MAX-1;
	int start;
	passes = 0;
	while(left<= right)
	{
	  passes++;
	  tostart = left+((key - a[left])*(right-left))/(a[right]-a[left]);
	  start = round(tostart);
	  if(a[start] == key)
		  return tostart;
	  else
		  if(a[start]<key)
			  left = tostart+1;
		  else
			  right = tostart-1;
	}
	return -1;
}
```

