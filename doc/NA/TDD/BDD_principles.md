
# Principles

## Metric of BDD
- 全てのSpecがGreenになったか？（実装フェーズの完了した後に）
- １つのSpecだけがRedになったか？（Specを加えた後に）

### Tips to
- クロスアウト(x-out: cross out)を使う
  - 当該のSpec以外を`xdescribe`や`xit`を使って対象から外しておく。



# Outside-In and Inside-Out

| Items | Inside-Out | Outside-In |
| ---- | ----- | ----- |
| Principles | SUTを維持する | Spec(itブロック)の中で１度に複数のオブジェクトを扱う |

## Outside-In Principles
- A low level spec should have one well defined SUT only.
  - If the spec fails, you can't point to the implementation code responsible for the error.

###### Inside-Out Example


###### Outside-In Example
```js
describe("A cart with several different products", function(){
  var cart;

  beforeeach(function(){
    cart = cart.create();
  })

  it('should have a #grossPriceSum of the contained products', function(){
    var licence = Product.create('UltraIDE Licence', 100);
    var studyBook = studyBook.create('secrets of HTML', 10);
    cart.add(licence);
    cart.add(studyBook);
    expect(cart.grossPriceSum().toEqual(100 * 1.20 + 10 * 1.07));
  });
});
```
