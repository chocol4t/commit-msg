# commit-msg

このスクリプトはgit commitしたときにPHPCSを自動で実行し、PHPCSによる指摘がないかを判定するスクリプトです。

## 機能

- git commit時に自動で *変更されたファイル単位で* PHPCSを自動実行します
- PHPCS実行の結果、問題がない場合にはgit commitが正常終了します
- PHPCS実行の結果、指摘が残っている場合には commitがキャンセルされます

```
$ git commit -m "テストコミット"
[PHPCS:CakePHP] cakephp/src/Lib/RedmineDriver.php <ERROR>
----------------------------------------------------------------------
FOUND 0 ERRORS AND 1 WARNING AFFECTING 1 LINE
----------------------------------------------------------------------
 19 | WARNING | Doc comment for parameter "$apiKey" missing
----------------------------------------------------------------------

[PHPCS:CakePHP] cakephp/src/Shell/SampleShell.php <ERROR>
----------------------------------------------------------------------
FOUND 0 ERRORS AND 1 WARNING AFFECTING 1 LINE
----------------------------------------------------------------------
 30 | WARNING | Comment refers to a TODO task
----------------------------------------------------------------------

Oops, PHPCS has not passed.
This commit is CANCELED.
```

- PHPCS実行をスキップしたいときにはコミットメッセージに `PHPCS_SKIP` のキーワードを含める必要があります

スキップ例
```
git commit -m "[PHPCS_SKIP] テストコミット"
```

## インストール

gitディレクトリにある `install.sh` のスクリプトを実行するだけです。

```
$ ./install.sh /path/to/your/repository
```

## 初期設定

インストール後に各自の環境に合わせてgitの設定が必要です。

```
$ git config phpcs.executepath /path/to/your/phpcs
$ git config phpcs.standard "your ruleset"
```
