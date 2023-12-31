# Linux

## OS
OS:オペレーティングシステム
コンピューターの基本的な機能を提供するソフトウェア
ex.ハードウェアの管理、メモリ管理など

## Linuxとは
OSの一種。UNIXを元に作られ、オープンソースのソフトウェアであるため無償で利用できる。

## カーネルとディストリビューション

## シェル

## Linuxの環境
- AWS Cloud9 で Linux 環境を構築する
- AWS で EC2 を立て、SSH で接続する
- ローカル PC 上に Docker や VirtualBox 等で Linux の環境を用意する
- パソコンに本体の OS とは別に Linux 環境を構築する。Windows なら WSL2、Mac ならデュアルブートや UTM を使用する
- パソコンに Linux をインストールする

## コマンド
現在のディレクトリ表示

`
pwd
`

ルートディレクトリに移動

`
cd /
`

ホームディレクトリに移動

`
cd
`

一つ上の親ディレクトリ

`
cd ..
`

ディレクトリの内容表示

`
ls
`

隠しファイル表示

`
ls -a
`

詳細なリスト形式表示

`
ls -l
`

ディレクトリの作成

`
mkdir hoge
`

ディレクトリの削除

`
rm -r hoge
`

`
rmdir hoge #ディレクトリ内にファイルがある場合、エラーとなる
`

ファイルの中身を出力  
`
cat hoge
`

ファイルの中身をスクロール表示  
`
less hoge
`

ファイルの作成  
`
touch README.md
`

ファイル名の変更  
`
mv hoge huga
`

ファイルのコピー  
`
cp hoge huga
`

ファイルの削除  
`
rm -r hoge
`

シンボリックリンク  
`
ln -s hoge huga
`

ファイルの検索   
`
find ~ -name hoge
`

検索   
`
grep '^a' hoge
`

## パーミッションの確認  
- 最初の1文字目はファイル種別(「-」:ファイル、「d」:ディレクトリ、「l」:シンボリックリンク)を表す
- 2文字目から4文字目はファイルの所有者に対する権限を表す
- 5文字目から7文字目はファイルの所有グループに対する権限を表す
- 8文字目から10文字目はその他に対する権限を表す
- r:読み込み、w:書き込み、x:実行

`
ll
`

`
ls -l
`

## パーミションの付与  

|　モード(数字)| モード(アルファベット)|権限|
|---|---|---|
|4|r|読み取り|
|2|w|書き込み|
|1|x|実行|

`
chmod 764 hoge.txt #chmod モード 対象ファイル名
`

|　変更対象|意味|
|---|---|
|u|ユーザー|
|g|グループ|
|o|その他|
|a|すべて|

|変更内容|意味|
|---|---|
|r|読み取り|
|w|書き込み|
|x|実行|

`
chmod u+x hoge.txt #chmod 変更対象 変更方法 変更内容 対象ファイル
`

## スーパーユーザー
- suの場合、一時的にroot権限を使えるようになる。rootのパスワードを使用。
- sudoの場合、コマンド単位で一時的にroot権限を使用する方法。自分自身のパスワードを使用。


## 標準入出力とは  
標準入力とは、プログラムが実行される際に割り当てられている入力用データのこと。標準出力とは、プログラムが実行された結果の出力先のこと。標準エラー出力とは、エラーメッセージの出力先である。

## リダイレクト  
リダイレクトとは、データの入力先や出力先を変更する機能  
`
ls / > ~/hoge.txt
`

## エラー出力のリダイレクト  
`
ls /hoge 2> ~/error.txt
`

## 出力とエラー出力のリダイレクト  
`
ls / hoge &> ~/result.txt
`

## /dev/null
/dev/nullとは、何を読み書きしても何も起きないようなデバイスファイル。/dev/nullに書き込まれたデータは全て破棄され、何もデータを返さない。 使い道は、コマンドやスクリプトを実行したときに出力される結果が不要であったり、出力されてほしくない場合に/dev/nullにリダイレクトする。

## /dev/null へのリダイレクト  
`
ls / > /dev/null
`

## パイプライン  
パイプラインとは、コマンドの出力を次のコマンドの入力として渡すこと  
`
ls / | grep '^l' #ルートディレクトリを ls コマンドで参照した結果のうち、"l" から始まるものだけを、パイプラインを使用して一回のコマンドで表示
`
## プロセス
- 一つ一つの処理を「プロセス」として管理されている
`ps #ログインしているユーザーのプロセスを表示`　　　
`ps aux #サーバー全体で稼働しているプロセスを表示`　　  
`sleep 100 & #コマンドの後ろに&をつけて実行するとバックグラウンド実行になる`　　
`kill プロセスID #プロセスを終了`

## シェルスクリプト
- シェルスクリプトの1行目には"#!/bin/bash"の文字列が必要
- 上記はbashによって解釈・実行されることを宣言している
- 変数は"変数名=値"の形で記載し、"$=変数名"で呼び出す
- 実行権限を付与して"bash ./script.sh"で実行する　　
### 「Hello World」と出力する
```
#!/bin/bash　　
STR="Hello World"　　
echo $STR　　
```

### 標準入力から値を受け取る
- 「read」は標準入力から受け取った内容を1行単位で変数に入れるコマンド　　
```
#!/bin/bash　　
read name　　
echo "Welcome $name"
```

### 条件分岐
```
#!/bin/bash

echo "Enter two numbers:"　　
read num1　　
read num2

echo "Choose an arithmetic operation (+, -, *, /):"　　
read operator　　
case $operator in　　
    +)　　
        result=$((num1 + num2))　　
        ;;　　
    -)　　
        result=$((num1 - num2))　　
        ;;　　
    \*)　　
        result=$((num1 * num2))　　
        ;;　　
    /)　　
        if [ "$num2" -eq 0 ]; then　　
            echo "Error: Cannot divide by zero."　　
            exit 1　　
        fi　　
        result=$(awk "BEGIN {printf \"%.2f\", $num1 / $num2}")　　
        ;;　　
    *)　　
        echo "Invalid operator"　　
        exit 1　　
        ;;　　
esac

echo "The result: $result"　　
```

### 繰り返し処理
for文　　
```
#!/bin/bash
for ((i = 1; i <= 100; i++)); do　　
  if ((i % 2 == 0)); then　　
    echo $i　　
  fi　　
done　　
```
while文　　
```
#!/bin/bash　　
num=1　　
while [ $num -le 100 ]; do　　
    if [ $((num % 2)) -eq 0 ]; then　　
        echo $num　　
    fi　　
    num=$((num + 1))　　
done　　
```
