## 2章
- 変数名はスネークケースで書く
```
special_price = 200
```
- ダブルクオートで囲むと\nが改行文字として機能する
- シングルクオートで囲むと文字列になる
- 式展開は#{}
```
name = 'Alice'
puts "Hello, #{name}!" #=> Hello, Alice!
```
```
# nを1増やす(n = n + 1と同じ)
n += 1 #=>2

# 文字列は数値に変換する必要がある
# 整数に変換
1 + '10'.to_i #=> 11
```
- falseまたはnilであれば偽
- それ以外はすべて真
- メソッド名はスネークケースで書く
- returnを使わない書き方のほうが主流。メソッドを途中で脱出する場合に使われる。
- andやorは条件分岐で使うのでなく、制御フローを扱うのに向いている
```
user.valid? && send_mail_to user # (user.valid? && send_mail_to) userとなり構文エラー
user.valid? and send_mail_to user # (user.valid?) && (send_mail_to user)と解釈される
```
- 条件演算子
```
n = 11
n > 10 ? '10より大きい' : '10以下'
#=> "10より大きい"
```
- ?で終わるメソッドは真偽値を返す
- !が付くメソッドは!が付かないメソッドよりも危険
- 非破壊的メソッドと破壊的メソッドの2種類が存在する場合は後者に!が付く(必ずしも破壊的メソッドではない)
```
# case文
case country # 対象のオブジェクトや式
when 'Japan'
  'こんにちは'　# 処理
else
  '???'
end
```
- Rubyの変数にはオブジェクトそのものではなく、オブジェクトへの参照が格納されている
```
# aとbは同じ文字列だが、オブジェクトとしては別物
a = 'hello'
b = 'hello'
a.object_id #=> 70182231931400
b.object_id #=> 70182236321960

# cにbを代入する。bとcはどちらも同じオブジェクト
c = b
c.object_id #=> 70182236321960
```
```
# Dateクラスは組み込みライブラリではないので、そのままでは使用できない
Date.today #=> Nameerror

# dateライブラリを読み込むとDateクラスが使えるようになる
require 'date'
Date.today
```
- 自作のRubyプログラムを読み込む場合は```require_relative```を使用する
- ```require_relative```では自ファイルからの相対パスで読み込むファイルを指定する
- putsメソッドは改行を加えて出力する
- printメソッドは改行を加えない
- pメソッドは改行を加えて出力する。文字列を出力すると、その文字列はダブルクオートで囲まれる
- ppメソッドは大きくて複雑な配列やハッシュ、オブジェクトの内容を見やすく整形して出力する
- putsメソッド、printメソッドは内部的にto_sメソッドを呼び出して変換されている
- pメソッドはinspectメソッドを呼び出している

## 第3章
- テストを自動化するためにテスト用のフレームワークを用いる(Minitest)
```
# テストコートの雛形
require 'minitest/autorun'

class SampleTest < Minitest:Test
  def test_sample
    assert_equal 'RUBY', 'ruby'.upcase
  end
end
```
- テストメソッドはメソッド名をtest_で始める
```
# aとbが等しければパスする
assert_equal b, a

# aが真であればパスする
assert a

# aが偽であればパスする
refute a
```
- テストコードは別ファイルに分け、```require_relative```でテストを行うファイルを参照する。

## 第4章
- <<を使うと配列の最後に要素を追加することができる
```
a = []
a << 1
a << 2
a << 3
a #=> [1, 2, 3]
```
```
# プロック処理
numbers = [1, 2, 3, 4]
sum = 0
numbers.each do |n|
  sum += n
end

# {}用いたブロック処理
numbers = [1, 2, 3, 4]
sum = 0
numbers.each { |n| sum+= n }
```
- 改行を含む長いブロックを書く場合はdo...end
- 1行でコンパクトに書きたいときは{}
```
# &とシンボルを使ってシンプルに書く
['ruby', 'java', 'python'].map { |s| s.upcase }
['ruby', 'java', 'python'].map(&:upcase)
```
1. プロックパラメータが1個だけである
2. ブロックの中で呼び出すメソッドには引数がない
3. ブロックの中では、ブロックパラメータに対してメソッドを1回呼び出す以外の処理がない
```
# 最後の値を含む
1..5
# 最後の値を含まない
1...5
```
