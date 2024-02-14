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
