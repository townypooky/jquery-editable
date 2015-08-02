# jQuery Editable Plugin
ある要素をクリックやダブルクリックですぐに編集、適用することができるようにします。

## 使い方
jQueryと`jquery.editable.js`をロードすれば使えます。
```js
<script src="//ajax.googleapis.com/ajax/libs/jquery/2.1.4/jquery.min.js"></script>
<script src="jquery.editable.min.js"></script>

```

`&lt;p&gt;`〜`/&lt;p&gt;`を編集するには、下記のようにします。
```js
$('p').editable('click', function(value, origin){
    // 変更をサーバーに送るには例えばこう
    $.ajax({
        url: './apply',
        data: 'p='+encodeURIComponent(value),
        success: function(){
            alert('ok');
        },
        error: function(){
            alert('error');
        }
    });
});
```

ダブルクリックで編集、フォームを`textarea`にするには、下記のようにします。
```js
$('p').editable({
    action: 'dblclick',
    multiline: true
}, function(value, origin){
    // 変更をサーバーに送るには例えばこう
    $.ajax({
        url: './apply',
        data: 'p='+encodeURIComponent(value),
        success: function(){
            alert('ok');
        },
        error: function(){
            alert('error');
        }
    });
});
```

編集で入力を空にすると削除できるようにも指定できます。
削除を有効にするには、第3引数で削除後のコールバック処理の指定が必須です。
```js
$('p').editable('dblclick', function(value, origin){
    // 変更をサーバーに送るには例えばこう
    $.ajax({
        url: './apply',
        data: 'p='+encodeURIComponent(value),
        success: function(){
            alert('ok');
        },
        error: function(){
            alert('error');
        }
    });
}, function(){
    // 削除したときの処理
    alert('Deleted');
});
```

スタイルシートは下記のように指定できます。
```css
p input.editable {
    /* inputのスタイル */
}

p textarea.editable {
    /* textareaのスタイル */
}
```

