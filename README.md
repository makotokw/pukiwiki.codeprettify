
pukiwiki.codeprettify.inc.php
====================

[PukiWiki](http://pukiwiki.sourceforge.jp/)で[google-code-prettify](http://code.google.com/p/google-code-prettify/)を利用してソースコードをハイライト表示するプラグインです。
google-code-prettify自体はjavascriptで動作します。

![codeprettify.inc.php](http://farm3.static.flickr.com/2706/4403915337_4120e669b7_o.jpg)

Install and Settings
====================

1. [pukiwiki.codeprettify](http://github.com/makotokw/pukiwiki.codeprettify/downloads)をダウンロードする

1. ファイルを解凍し、codeprettify.inc.phpをpluginフォルダの下に配置する

1. google-code-prettifyをダウンロードする

    <http://code.google.com/p/google-code-prettify/> から、下記のいずれかをダウンロード:
  
        prettify-{日付}.zip
        prettify-small-{日付}.zip
        
    smallがついてるのはコメントや改行などを縮小化したバージョンで機能的にはどちらも同じ、コードに興味がある人は前者、 とりあえず使えればいいやという人は後者でよい。

1. google-code-prettifyのzipファイルを解凍し、下記ファイルをskinフォルダの下に置く

        prettify.css
        prettify.js

1. skin/pukiwiki.skin.phpファイルを編集し、google-code-prettifyのcssファイルとjsファイルを追加する

        <link rel="stylesheet" type="text/css" media="print"  href="skin/pukiwiki.css.php?charset=<?php echo $css_charset ?>&amp;media=print" charset="<?php echo $css_charset ?>" />

    の下あたりに下記を追加  
     
        <link href="skin/prettify.css" rel="stylesheet" type="text/css" charset="utf-8"/>
        <script src="skin/prettify.js" type="text/javascript" charset="utf-8"></script>

    さらにbodyタグを以下のように変更する

        <body onload="prettyPrint();">

1. 複数行の引数を有効にする

    pukiwiki.ini.phpを編集し、**PKWKEXP_DISABLE_MULTILINE_PLUGIN_HACK**のdefineを探して、値を0にする

        define('PKWKEXP_DISABLE_MULTILINE_PLUGIN_HACK', 0); // 1 = Disabled

How to use
==========

ブロック型とインラインの両方に対応しています

ブロック型
-------

    #codeprettify{{
    <?php
    echo 'test';
    ?>
    }}

インライン型
---------

    &codeprettify{<?php echo 'test'; ?>};
    

cssクラスの追加
----------

google-code-prettifyでは言語の指定や、行数の表示がcssクラスの指定で行えます。 
codeprettifyプラグインでは関数の第一引数で追加するcssクラス指定できます。

    #codeprettify(lang-html linenums:4){{
    <body>
    <h1>codeprettify</h1>
    </body>
    </html>
    }}

History
=======

v1.1 at 2010/12/19
------------------
 - google-code-prettifyのオプション指定のためにcssクラスの追加に対応

v1.0 at 2008/09/25
------------------
 - 初リリース

See Also
========
- <http://pukiwiki.sourceforge.jp/?%E8%87%AA%E4%BD%9C%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3/codeprettify.inc.php>


Copyright and Software License
==============================

<http://www.gnu.org/licenses/gpl.html>  GPLv2

Copyright 2008-2010, makoto_kw (<http://www.makotokw.com>)

