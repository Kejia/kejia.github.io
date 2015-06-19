    Title: take-while of clojure
    Date: 2015-06-19T10:20:23
    Tags: clojure

in clojure, `take-while' is similar to `filter', but they are different.

<!-- more -->

```clojure
> (filter pos? [8 0 -1 2 -3])
(8 2)
> (take-while pos? [8 0 -1 2 -3])
(8)
```

`take-while' stops traversing the list when the predicate is false.
