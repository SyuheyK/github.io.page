---
title: "Mecabの使い方のまとめ"
tags: ["自然言語処理"]
date: 2020-01-27T10:00:00+09:00
draft: false
---

## インストール方法
以下を参照．

## 設定ファイルの場所
環境によって異なるので注意．

https://ichibariki.hatenablog.com/entry/2017/01/09/150542
https://obel.hatenablog.jp/entry/20170218/1487418388

## ユーザ辞書の追加
https://m0t0k1ch1st0ry.com/blog/2016/06/04/mecab/


{{< highlight shell>}}
/usr/local/Cellar/mecab/0.996/libexec/mecab/mecab-dict-index \
-d /usr/local/lib/mecab/dic/mecab-ipadic-neologd \
-u /usr/local/lib/mecab/dic/userdic/user_dic.dic \
-f utf-8 \
-t utf-8 \
./user_dic.csv
{{< / highlight >}}
オプションの説明は以下のとおり．
|コマンド|内容|
|:---:|---|
|-d DIR:| システム辞書があるディレクトリ|
|-u FILE:| FILE というユーザファイルを作成|
|-f charset:| CSVの文字コード|
|-t charset: |バイナリ辞書の文字コード|

処理結果が
{{< highlight shell >}}
reading ./tailoring_dic.csv ... 1
emitting double-array: 100% |###########################################| 

done!
{{< / highlight >}}
と， `done!` の文字が出力されればOK．
その後， `/usr/local/etc/macabrc` に以下の1行を追加し，ユーザ辞書の設定が読まれる様にする．
{{< highlight shell>}}
userdic = /usr/local/lib/mecab/dic/userdic/user_dic.dic 
{{< / highlight >}}


## pythonからのユーザ辞書の利用方法
Taggarのオプションに `-u` でユーザ辞書のpathを追加する．
{{< highlight shell>}}
import MeCab
mecab = MeCab.Tagger ('-d /usr/local/lib/mecab/dic/mecab-ipadic-neologd -u /usr/local/lib/mecab/dic/userdic/user_dic.dic')
{{< / highlight >}}

