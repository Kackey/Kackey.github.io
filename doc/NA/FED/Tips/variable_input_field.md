
* 追加のフィールドのHTMLテンプレートはjsRender等のテンプレートエンジンを使う
* 入力された値の最終的な集約には、絶対指定（id/name）を使わず、相対指定する。
  * jQueryで`children().each()`とか

###### できたらいいな
* form使わないで、HTTPリクエストを直接JSから発信する
  * form使うと、パラメータのぶんだけ予め<input>フィールドを用意する必要があり面倒。
* 全部をJSフレームワークで作っちゃう。Mithrilとか。
  * HTMLテンプレートも含めてコンポーネントとして扱える

# Reference
* [JavaScriptのテンプレートJsRenderとJsViewsの紹介 - Qiita](http://qiita.com/mima_ita/items/628bf36dd453cf85bf7d)
* [徹底解説JsRender／JsViews一覧：CodeZine（コードジン）](http://codezine.jp/article/corner/496)
* (official) [JsRender/JsViews](http://www.jsviews.com/#getstarted)
