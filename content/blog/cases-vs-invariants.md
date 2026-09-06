---
title: "Cases vs Invariants"
description: "How I wrote diabolical code using case-based approach, then made it simple and less diabolical using invariant-based reasoning"
tags:
  - algorithms
  - problem-solving
---

I stumbled upon a [situation](https://leetcode.com/problems/find-median-from-data-stream)
where I learnt about **_invariants_** to write less diabolical code.

> When I talk about **_case-based-reasoning_** I mean approaching a problem by breaking it down into cases
> ie., **_if this happens do this, if that happens do that_**
>
> You read more about [invariants here](<https://en.wikipedia.org/wiki/Invariant_(computer_science)>)
> they probably have a nice explanation over there.
> It basically means a condition or a property that must be **_true_** and **_always true_** throughout the algorithm.

Now, let's take the [situation](https://leetcode.com/problems/find-median-from-data-stream)
ie., finding the [median](https://en.wikipedia.org/wiki/Median) in the **_stream of data_**.

<br>

## The Situation

<br>

We would start out with an **_empty array or a slice_** and we need to implement
a couple of methods ie., adding a number and returning the median at that time.

So, to find the median we can either **_sort_** the array each time
or we can **_traverse_** through the array, to find the **_right position_** to insert the number
and **_move all the other elements_** to the right.

That brings us to either **_O(n log n)_** or **_O(n)_** for each insertion,
and **_O(1)_** for returning the median.

And yeah, we can do **_better_**.

So the trick is to use [heaps or priority queues](<https://en.wikipedia.org/wiki/Heap_(data_structure)>).

We would maintain two heaps:

- The **_maxheap_** the smaller half.
- The **_minheap_** the bigger half.

And this is where the **_invariants_** come in:

- The heaps **_differ in size_** by at most **1**.
- **_Every element_** in the **_minheap_** is **_less than_** or **_equal_** to **_every element_** in the **_maxheap_**.

So whenever we need the **_median_** we can do:

- If there are **_odd_** number of elements, the median is the **_root_** of the maxheap.
- If there are **_even_** number of elements, the median is the **_average of the roots_** of both the heaps.

![examples of arrays, implementing the invariants](/cases-vs-invariants-the-situation.jpg)

<br>

## The Solution

<br>

Before implementing `AddNum` we must implement things required for it.

Since we need heaps and I wrote it.
**_Go_** has [container/heap](https://pkg.go.dev/container/heap)
and it expects us to satisfy [heap.Interface](https://pkg.go.dev/container/heap#Interface).

```go
package main

type minheap []int

func (h *minheap) Len() int { return len(*h) }
func (h *minheap) Less(i, j int) bool { return (*h)[i] < (*h)[j] }
func (h *minheap) Swap(i, j int) { (*h)[i], (*h)[j] = (*h)[j], (*h)[i] }

func (h *minheap) Push(x any) {
	(*h) = append((*h), x.(int))
}

func (h *minheap) Pop() any {
	n := len(*h)
	x := (*h)[n-1]
	*h = (*h)[:n-1]
	return x
}

type maxheap []int

func (h *maxheap) Len() int { return len(*h) }
func (h *maxheap) Less(i, j int) bool { return (*h)[i] > (*h)[j] }
func (h *maxheap) Swap(i, j int) { (*h)[i], (*h)[j] = (*h)[j], (*h)[i] }

func (h *maxheap) Push(x any) {
	(*h) = append((*h), x.(int))
}

func (h *maxheap) Pop() any {
	n := len(*h)
	x := (*h)[n-1]
	*h = (*h)[:n-1]
	return x
}
```

Now that we have the `minheap` and the `maxheap` we can move on to implementing `MedianFinder`.

```go
package main

type MedianFinder struct {
    // maxheap contains the smaller half of the numbers.
    // Its root is the largest number in the smaller half.
    minheap *minheap

    // minheap contains the bigger half of the numbers.
    // Its root is therefore the smallest number in the bigger half.
    maxheap *maxheap
}

// Constructor returns a MedianFinder,
// in other words a instance of medianFinder.
func Constructor() MedianFinder {
    return MedianFinder{
        minheap: &minheap{},
        maxheap: &maxheap{},
    }
}

// FindMedian returns the median of the array.
func (this *MedianFinder) FindMedian() float64 {
    // when there are odd number of elements,
    // maxheap has one more element than minheap
    // so its root is the middle element
    if n := (*this.maxheap).Len() + (*this.minheap).Len(); n%2 == 1 {
        return float64((*this.maxheap)[0])
    }

    // when there are even number of elements,
    // the roots of the both the heaps are the middle elements
    // so we return their average.
    l := (*this.maxheap)[0]
    r := (*this.minheap)[0]
    return float64(l+r) / float64(2)

}
```

<br>

## Case Based Reasoning

<br>

Now that we have our pre-requisites we can move on to implement `AddNum`.
`AddNum` has a **_simple responsibility_**, add a number while keeping the **_invariants true_**.

Don't worry it'll look diabolical, but actually it is simple.

```go
func (this *MedianFinder) AddNum(num int) {
    // if both the heaps have the same number of elements
    // maxheap reaceives the new element,
    // so that the sizes become:
    //   - maxheap (n/2) + 1
    //   - minheap (n/2)
    // then we can just return the root of the maxheap
    // since that is the required median
    if (*this.maxheap).Len() == (*this.minheap).Len() {
		var bound int
		if (*this.maxheap).Len() == 0 {
			bound = math.MaxInt
		} else {
			bound = (*this.maxheap)[0]
		}

		if num < bound {
			heap.Push(this.maxheap, num)
		} else {
			heap.Push(this.minheap, num)
			x := heap.Pop(this.minheap)
			heap.Push(this.maxheap, x)
		}

        return
    }

    // if the control flow reaches here
    // it means the heaps differ is sizes
    // ie., that the sizes become (because of the previous statements):
    //   - maxheap (n/2) + 1
    //   - minheap (n/2)
    // so minheap reaceives the new element,
    // then both the heaps equals in sizes
    // and for the median we can return the average of teh roots
    var bound int
    if (*this.maxheap).Len() == 0 {
        bound = math.MinInt
    } else {
        bound = (*this.maxheap)[0]
    }

    if bound < num {
        heap.Push(this.minheap, num)
    } else {
        heap.Push(this.maxheap, num)
        x := heap.Pop(this.maxheap)
        heap.Push(this.minheap, x)
    }
}
```
