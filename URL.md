2026-02-07
# URL（Uniform Resource Locator）
http://から始まるものが有名だが、他にもftp:// file:// mailto:// など色々ある
### 例
```
http://user:password@www.sample.com:80/dir/file.html
```
## URI（Uniform Resource Identifer）
対象のデータやファイルのパスのことを指す
場所を指定するので絶対パス、相対パスでもURIとなりえる
※逆に相対パスはURLにはならない
## メソッド
対象のデータ・ファイルに対して行いたい動作を指定する
GET/POSTが有名
| メソッド    | 主な用途          |
| ------- | ------------- |
| GET     | リソースの取得       |
| POST    | リソースの作成／処理の実行 |
| PUT     | リソースの全体更新     |
| PATCH   | リソースの部分更新     |
| DELETE  | リソースの削除       |
| HEAD    | ヘッダーのみ取得      |
| OPTIONS | 利用可能なメソッドの取得  |
| TRACE   | リクエスト経路の確認    |
| CONNECT | 通信トンネルの確立     |

