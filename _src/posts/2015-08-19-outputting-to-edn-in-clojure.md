    Title: outputting to edn in clojure
    Date: 2015-08-19T11:08:37
    Tags: clojure, edn

```clojure
(spit "/xi/xii.edn" (with-out-str (clojure.pprint/pprint x)))
```
