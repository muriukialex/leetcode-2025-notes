# k frequent words

```js
var topKFrequent = function (words, k) {
    let map = {};

    for (let word of words) {
        if (map[word] === 0) {
            map[word] = 1;
        } else {
            map[word] = map[word] + 1;
        }
    }

    let sorted = Object.keys(map).sort((a, b) => {
        if (map[a] === map[b]) {
            // check if a comes before or after b, sort in lexicographic order, eg. "alex" comes before "miriam"
            return a.localeCompare(b);
        }
        // sort in ascending order
        return map[b] - map[a];
    });

    return sorted.slice(0, k);
};
```

go through the list of words

place the words in a hash map with word as the key and frequency as the value of the word

sort the hashmap, using the words frequency values, if the words frequency is same, sort by lexicographic order

return sorted array of words, from first element to element k
