# TIM SORT 

### Concept of Tim sort-

Tim sort is the fastest algorithm implemented popularly in Python libraries and later in Java and other languages. In reality we observe that insertion sort is the fastest sorting algorithm in case of smaller elements instead of quick sort or merge sort mainly because the constant factor of the asymptotic complexity is lesser in case of insertion sort than in quick sort which means is even if quick sort is a small task we need to do it more times than insertion sort which is a huge task that needs to be done less number of times. So if we divide an array into smaller parts, we can apply insertion sort on little buckets And we can merge these buckets to form a full sorted array. 


### Concept of runs-

 Often while sorting we see that few elements in an array are already in some sort of sorted sequence. For example in array- 10 17 9 -5 6 15 12 we see that 10 17 are sorted 9 -5 are sorted in decreasing order. -5 6 15 are sorted and so on. (when I say sorted I generally mean in increasing order. A decreasing order sort is just an increasing order sort reversed). These short sorted sequences are called runs. 


### Concept of merge

In order to merge our sorted sequences we can use the merge sort algorithm and we know that merge sort is fasted when used on 2 equal sized arrays. (Merge sort means merging of 2 sorted arrays not the whole partitioning thing). So if we build runs of same size from an array, put them on a stack and pick 2 top elements from the stack and keep merging them till the stack is empty, we will find our array sorted. So far, this is a modified Bucket sort



### Various optimisations to Tim Sort listed below- 

#### Empirical stats- 
If the array is less than 32 elements in size or 64 elements in size, TimSort will apply insertion sort on those elements. 

#### Optimizing the insertion
Binary insertion sort- insertion sort picks up an element, performs linear search and puts them in the right place. Binary insertion sort on the other hand does the same but using Binary search instead of linear search. 

#### Optimizing run selection
Tim sort realises that setting equal size of the runs (increasing or decreasing sequences) will not be a good idea since these runs can potentially go longer than that and less the number of runs, lesser is the size of the merge tree. So it sets a minimum size of each run. Meaning, a run can be let's say 3 elements long at least. But if it goes any longer than that, it is acceptable. In order to do this, Tim sort iterates over an array and finds a pattern in the array (either increasing or decreasing) till either the minimum size is satisfied or the pattern goes on 

#### The stack
In order to satisfy the minimum size requirement of each run, Tim sort uses binary insertion sort to sort at least 3 elements (considering a run size of 3) and put the runs on the stack. What that intuitively means is, it efficiently sorts chunks of an array which might already be sorted to some extent and then merges the chunks. The stack stores the runs and is a ledger of how much data is already sorted or run over in the given array

#### Space optimization
We know that Merge sort can use a lot of space unnecessarily because it creates a temporary array of all elements it needs to merge (m+n size). Instead, Tim sort creates a temporary array of size minimum of m and n and shifts the remaining elements to one direction and then runs the merge operations effectively doing part of the work in-place. 

#### Merge balancing
Now we know that picking up sorted runs from the stack is a big operation, so Tim Sort can use another optimisation to solve that. We realise that runs can be of unequal size and merge is efficient for equal size, so it runs a sorting on top 3 elements and merges the 2 smallest to a bigger size so that the bigger merge comes closer to the largest element on the stack. 

### Putting it all together 
Take the array, if the size is less than 32, just use insertion sort. If the size is more, find runs. If the runs are decreasing reverse them. If you can't find runs, iterate till the minimum size and keep inserting them in the correct position using binary insertion sort. Put the runs on a stack. Pick top elements from the stack and keep merging them and putting them back on the stack till the stack is empty execpt for the sorted array. 

------------------------------------------
