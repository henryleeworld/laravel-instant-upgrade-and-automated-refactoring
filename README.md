# Laravel 12 即時升級和自動重構

引入 driftingly 的 rector-laravel 套件來擴增即時升級和自動重構，透過套用規則來自動化修改、重構及掃描程式碼。

## 使用方式
- 把整個專案複製一份到你的電腦裡，這裡指的「內容」不是只有檔案，而是指所有整個專案的歷史紀錄、分支、標籤等內容都會複製一份下來。
```sh
$ git clone
```
- 將 __.env.example__ 檔案重新命名成 __.env__，如果應用程式金鑰沒有被設定的話，你的使用者 sessions 和其他加密的資料都是不安全的！
- 當你的專案中已經有 composer.lock，可以直接執行指令以讓 Composer 安裝 composer.lock 中指定的套件及版本。
```sh
$ composer install
```
- 產生 Laravel 要使用的一組 32 字元長度的隨機字串 APP_KEY 並存在 .env 內。
```sh
$ php artisan key:generate
```
- 當指定 `--dry-run` 參數，可以在不實際執行變更的情況下協助檢查了目錄中是否有需要修改的程式碼。
```sh
$ ./vendor/bin/rector process {目錄} {--dry-run}
```
----

## 畫面截圖
![](https://i.imgur.com/lo9GyP1.png)
> 在對外的介面上沒有做改變、介面背後的對應行為也沒有改變的情況下，基於可讀性，以及日後更便於修改的目的之下，來評估改寫內部的程式碼實作
