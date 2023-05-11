# 概要(Overview)
ここに概要を書いてね
Please write PR overview down here.

## 確認項目

プルリクを作成する前、以下の項目を確認してチェックしてください。

### 毎回必ずチェックしてください。

* [ ] 修正・追加した箇所を動作確認したか
* [ ] 誤字脱字がないか
* [ ] php-cs-fixerコマンドの実行を確認したか

### 必要がある場合はチェックしてください。

* [ ] 共通メソッドを修正・追加した場合、各呼び出し先でちゃんと以前の通り（あるいは意図した通り）動作しているか
* [ ] table構造を変更・作成した場合、利用している箇所でちゃんと以前の通り（あるいは意図した通り）動作しているか
* [ ] 変更箇所とその類似箇所との統一性が保たれているか
* [ ] migrationを追加した場合、$php artisan migrate:refreshが成功することを確認したか

## Items to check

Before creating a pull request, please check the following items:

### Please check everytime below 3 items.

* [ ] Did you confirm the operation of the changed or added parts?
* [ ] Did you confirm php-cs-fixer command execution ?
* [ ] Is there no typographical error?
### Please only check if applicable below 3 items.

* [ ] If common methods are modified or added, will each callee work as it did before (or as intended)?
* [ ] If the table structure is modified or created, is it still working correctly (or as intended) where it is used?
* [ ] Is consistency maintained between the changed part and its similar parts?
* [ ] If you added migration, did you confirm that "$ php artisan migrate:refresh" succeeds?
