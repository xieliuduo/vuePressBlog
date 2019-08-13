## 闭包在多个异步函数这种的计数用法，当然你可以使用 promise.all

```js
(function() {
  var count = 0;
  var result = {};

  $.get("http://data1_source", function(data) {
    result.data1 = data;
    count++;
    handle();
  });
  $.get("http://data2_source", function(data) {
    result.data2 = data;
    count++;
    handle();
  });
  $.get("http://data3_source", function(data) {
    result.data3 = data;
    count++;
    handle();
  });

  function handle() {
    if (count === 3) {
      var html = fuck(result.data1, result.data2, result.data3);
      render(html);
    }
  }
})();
```
