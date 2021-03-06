# messy string

ランダムな文字列を生成するツール

## インストール

```
pip install messy-string
```

## 概要

パラメータテンプレートに沿ってランダムな文字列を生成するツール．
パラメータテンプレートは以下の形式をしている．
```
{
    'string_type': {
        'hex': True,
        'decimal': False,
        'character': False,
        'symbol': False,
        'options': ''
    },
    'option': 'lowercase',
    'length': 8,
    'number': 1
}
```

- `string_type`: 使用する文字の設定．`True`になっているものと`options`に設定した文字列を使う．
  - `hex`: `0123456789abcdef`を使う
  - `decimal`: `0123456789`を使う
  - `character`: `a`から`z`の文字列を使う
  - `symbol`: `!"#$%&\'()*+,-./:;<=>?@[\\]^_{|}~`これらの記号プラス「`」を使う
  - `options`: ここに設定した文字列を使う
- `oprion`: 大文字小文字の設定
  - `lowercase`: 小文字のみ
  - `uppercase`: 大文字のみ
  - `loweruppercase`: 大文字と小文字を両方使う
- `length`: 文字列の長さ
- `number`: 生成する文字列の個数

## 使い方

### コマンドラインから

```
$ messy_string -h
usage: messy_string [-h] [--hex] [-d] [-c] [-s] [-o OPTIONS] [-lo] [-up]
                     [-lu] [-l LENGTH] [-n NUMBER] [-P PARAMETER] [-Pl]

radioの管理を行うプログラム

optional arguments:
  -h, --help            show this help message and exit
  --hex                 16進数(default)
  -d, --decimal         数値を使用する
  -c, --character       文字列を使用する
  -s, --symbol          記号を使用する
  -o OPTIONS, --options OPTIONS
                        任意の文字列
  -lo, --lowercase      小文字にする(default)
  -up, --uppercase      大文字にする
  -lu, --loweruppercase
                        大文字と小文字を両方使う
  -l LENGTH, --length LENGTH
                        長さ
  -n NUMBER, --number NUMBER
                        出力する個数
  -P PARAMETER, --parameter PARAMETER
                        パラメータを指定
  -Pl, --parameter_list
                        利用できるパラメータの種類
```

- オプションによりパラメータを調整する．
- `-Pl`により内蔵されているパラメータのリストを表示することができる．
- `-P`により内蔵されているパラメータを使ってランダムな文字列を生成することができる．

### モジュールとしてインポート

```
import messy_string

print(messy_string.RSParam.get_param_list())   # パラメータテンプレートを表示
print(messy_string.RSParam.RSP_ID)             # RSP_IDパラメータの詳細を表示
print(messy_string.messy_string(messy_string.RSParam.RSP_ID)) # RSP_IDパラメータを使用してランダム文字列を生成
```

`messy_string.messy_string()`メソッドにパラメータを渡すことでランダムな文字列を作成できる．
なお，内蔵パラメータは`RSParam`で定義されている．