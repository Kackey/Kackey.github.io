

# Plugins
* Japanese-wrap
* file-icons
* Project Manager
* color-picker
* minimap


# Style Sheet
`File` -> `Open Your Stylesheet`

## エディタ
###### 選択箇所の背景色変更
```css
atom-text-editor::shadow {
  .gutter .cursor-line {
    background-color: fade(cyan, 15%);
  }
  .highlights {
    .selection .region {
      background: fade(yellow, 20%);
    }
    .find-result .region {
      border: 1px solid fade(yellow, 80%);
    }
  }
}
```
## Markdownプレビュー
```css
.markdown-preview {
  font-family: "Consolas", "メイリオ", "Source Han Code JP"; h1, h2, h3, h4, h5, h6 {font-family: "メイリオ";};
  color: #000000;
  background-color: #ffffff;
  // letter-spacing: 0.08em;
  h1 {
    font-size: x-large;
    font-weight: bold;
    color: #000000;
    background-color: #e2e2e2;
    line-height: 1.4;
    padding: 5px 10px;
    border-radius: 5px;
  }
  h1:first-child{
    padding-top: 10px;
  }

  h2 {
    font-size: x-large;
    font-weight: bold;
    color: #000000;
        line-height: 1.4;
    padding: 5px 10px;
    border: 1px solid #e2e2e2;
    border-left: 10px solid #e2e2e2;
    border-radius: 5px;
  }

  h3 {
    font-size: x-large;
    color: #000000;
    font-weight: bold;
        line-height: 1.2;
    padding: 5px 10px;
    border-left: 10px solid #e2e2e2;
    border-bottom: 1px solid #e2e2e2;
    border-radius: 5px;
  }
  h4 {
    font-size: large;
    line-height: 1.2;
    padding: 5px 10px;
    border-left: 10px solid #e2e2e2;
    border-radius: 5px;
  }
  h5 {
    font-size: large;
  }
  h6 {
    font-size: medium;
  }

  table th {
    background-color: #919191;
    color: #000000;
  }
  table tr {
    background-color: #ffffff;
  }
  table tr:nth-child(2n) {
    background-color: #e2e2e2
  }
}
```

# Reference
- [［捗］Markdown便利！～GitHub謹製のテキストエディタAtomはWindows、Mac、Linuxで利用可能 | 捗りあん](http://hakadorian.com/archives/2116)
  - Markdownプレビューの表示変更方法とか。
* [Atom がヤバイ！SublimeTextを余裕で凌駕してしまっていた件](http://www.geeks-dev.com/atom-%E3%81%8C%E3%83%A4%E3%83%90%E3%82%A4%EF%BC%81sublimetext%E3%82%92%E4%BD%99%E8%A3%95%E3%81%A7%E5%87%8C%E9%A7%95%E3%81%97%E3%81%A6%E3%81%97%E3%81%BE%E3%81%A3%E3%81%A6%E3%81%84%E3%81%9F%E4%BB%B6/)
