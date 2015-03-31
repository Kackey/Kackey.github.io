# [Title] e2e Test Practice

# Page Objects

```javascript
var Hoge_page = function () {
  this.loadPage = function(){ browser.get('http://hoge.co.jp/hogehoge/'); };
  this.getUrl = function(){ return browser.getCurrentUrl(); };
  this.getTitle = function(){ return browser.getTitle(); };
  this.payment_input = function(){ return $("[name=payment]"); };
  this.submit_btn = function () { return $("#mainContentArea > div.contents-sub > div.container.container01 > div.content > form > div:nth-child(3) > input"); };

  this.should = {
    title: 'By the hoge, for the hoge, ',
    url: 'http://hoge.co.jp/hogehoge/'
  };
};
```

# Naming Rule

###### UI parts
- Button: xxx_btn
- Input: xxx_input

# Tips
###### Clear value
Sometimes browser automatically fulfill input field.

```js
${element}.clear

$("input[name=hoge]").clear();
```
