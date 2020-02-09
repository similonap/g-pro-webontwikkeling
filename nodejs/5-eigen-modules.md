# 05. eigen modules

## search-string

```javascript
const search = ['antwerpen', 'brussel', 'leuven', 'mechelen', 'gent'];

exports.getSearchTerm = function () {
  const id = Math.floor(Math.random() * search.length);
  return search[id];
};
```



