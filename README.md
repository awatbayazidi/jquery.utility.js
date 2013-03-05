これはメソッドチェイン内でいくつかの機能を使えるようにした jQuery プラグインです。

# 機能説明

## .create( _tagName_, _elements_ )
.create() は、ほぼ .append() と似ていますが、生成する方法が異なります。

第一引数 _tagName_ は、'div' や 'span' などのタグ名を記載します。

第二引数 _elements_ は、生成する要素に与えるデータを Object 形式で定義します。
'css' の場合は、$(selector).css({color: 'rgb(255, 0, 0)'}) と同じ形式です。font-size などハイフンが入る値の場合は、css: {'font-size': '1.2em'} のように引用符で囲んでください。
'data' の場合は、data: {name: 'user name'} のように Object 形式で指定します。name-01 などハイフンが入る値の場合は、data: {'name-01': 'user name 01'} のように引用符で囲んでください。
また、上記以外の場合、スラッシュで区切ることで、同じ値を複数の属性に定義できます。

$('body').create('input', {id: 'name', type: 'text', data: {name: 'user name'}, css: {color: 'rgb(255, 0, 0)'}, 'placeholder/title/value': 'Fill in your name'});


## .tx( _string_ )
.tx() は、要素に title と html に同じ値を入れたい場合などに使用できます。

img 要素と input 要素（type:image）に使う場合は、alt と title に string が入ります。
input 要素（type:text）、input 要素（type:search）、input 要素（type:url）、input 要素（type:tel）、textarea 要素に使う場合は、title と placeholder に string が入ります。
その他の場合は title と html に string が入ります。

強制的に上記の 2 つの属性に string が入るので、個別に指定したい場合は、.tx() を使わず、.attr() などで個別に指定してください。

$('span').tx('This is a test.');


## .changeClass( _remove_, _add_ )
.toggleClass() は、あれば削除、なければ追加をしますが、.changeClass() は、強制的に第一引数を削除、第二引数を追加します。

$('p').changeClass('fadeIn', 'fadeOut');


## .isMobile( _target_ )
.isMobile() は、アクセスしたデバイスがモバイルかどうかを UserAgent で判定します。引数 _target_ が以下の場合、次のような挙動になります。

* 与えられない場合：iPhone/iPad/iPod/Android であるかの結果を true/false で返します。
* 'iPhone' の場合：iPhone であるかの結果を true/false で返します。
* 'iPad' の場合：iPad であるかの結果を true/false で返します。
* 'iPod' の場合：iPod であるかの結果を true/false で返します。
* 'iOS' の場合：iPhone/iPad/iPod であるかの結果を true/false で返します。
* true の場合：iPhone/iPad/iPod/iOS であるかの結果を Object 形式で返します。

if ($().isMobile('iPhone')) alert('You use iPhone');


## .isMail( _value_ )
.isMail() は、判定する値がメールアドレスかどうか（xx@xx.xx）を true/false で返します。引数 _value_ が以下の場合、次のような挙動になります。

* 与えられている場合：その与えられた value がメールアドレスかどうかの判定をします。
* 与えられない場合：$(this).val() を値として、メールアドレスかどうかの判定をします。

if (!$('#input_name').isMail()) alert('Check the email address');


## .doScroll( _target_ )
.doScroll() は、画面スクロールを行います。引数 _target_ が以下の場合、次のような挙動になります。

* 与えられている場合：target の場所を position() で取得し、スクロールします。
* 与えられない場合：ページの一番上（x: 0, y: 0）へスクロールします。

$().mobile() で true と判定された場合は、上記の場所へのスムーススクロールのアニメーション無しのジャンプになります。

$().doScroll();


## .addJS( _file_ )
.addJS() は、head 要素の一番最後に JavaScript ファイルを追加します。

$().addJS('./test.js');


## .addCSS( _file_ )
.addCSS() は、head 要素の一番最後に CSS ファイルを追加します。

$().addCSS('./test.css');


## .print( _target_ )
.print() は、console.log() を行います。引数 _target_ が以下の場合、次のような挙動になります。

* 与えられている場合：console.log(target) を実行します。
* 与えられない場合：concole.log($(this)) を実行します。



# 動作環境
Chrome/Safari/Firefox/Opera/IE8+
iPhone/iPad/iPod touch/Android


このプラグインがお役に立てれば幸いです。