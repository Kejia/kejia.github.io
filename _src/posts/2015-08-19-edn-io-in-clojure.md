    Title: edn io in clojure
    Date: 2015-08-19T11:19:51
    Tags: clojure, edn

output:

```clojure
(spit "/xi/xii.edn" (with-out-str (clojure.pprint/pprint x)))
```

input:

```clojure
(read-string (slurp "/xi/xii.edn"))
```
