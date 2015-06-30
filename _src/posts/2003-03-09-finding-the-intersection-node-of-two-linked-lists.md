    Title: finding the intersection node of two linked lists
    Date: 2003-03-09T08:06:51
    Tags: algorithm, 算程

_finding out the intersection of two linked lists can be solved by this interesting algorithm._

<!-- more -->

> there are 2 linked lists, and they may intersect at some node. for example,
> 1 → 2 → 3 → 4 → 5
>       6 ↗
> list 1 → 2 → 3 → 4 → 5 and 6 → 3 → 4 → 5 have the intersection node 3.
> find out the intersection node if any.

here is an $O(n)$ time and $O(1)$ space algorithm. the basic idea is using 2 pointers to traverse the lists. firstly, the 2 pointers point to the heads of the lists respectively. they go through the lists step by step. one case is that the pointers point to the same node before arrive the tails, and that node is the intersection node. one of the other cases is that one pointer arrives a tail while another one not. then, assign the pointer to tail to the head of another list, and continue the process. if the lists intersect, the pointers must encounter at the intersection node. if they do not intersect, the pointers must point to a tail or the tails at some moment.
