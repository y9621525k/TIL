## select

```
mysql> select * from board;
#rails version
Board.all
```

## where

```
mysql> select * from board where user_id = 1;
#rails version
Board.where(user_id: 1)
```

## join

```
#あるテーブルとあるテーブルを結合する
mysql> select * from user inner join board;
```

## on

```
#結合条件を指定する
mysql> select * from user inner join board on user.id = board.user_id;
#rails version
User.joins(:boards)
```

## order

```b
#表示するレコードの並び順を指定
mysql> select * from board order by title asc;
#rails version
Board.all.order(title: :asc)
```

## update

```
#レコードの内容を更新
mysql> update user set first_name="hoge" where id = 1;
#rails version
user.update(first_name: 'hoge') # userはidが1のユーザーという前提
```

## delete

```
#レコードを削除
mysql> delete from user where id = 3;
#rails version
user.destroy # userはidが3のユーザーである前提
```

1.filmsテーブルからtitleの一覧を取得する
```
SELECT title form films;
```
