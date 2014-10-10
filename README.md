# Atrantic Cloud VPS setup 
Atrantic Cloud VPSをセットアップするためのansibleスクリプトです。
Ubuntuでrootが取れるサーバーであればAtranticのVPSでなくても動くかと。

## やること
 * SSHのポート変更
 * ログインユーザー作成
 * 鍵交換
 * レポジトリ更新・追加
 * 

## 使い方

__設定__

```hosts/host``` ファイルに対象サーバーのIPを列挙してください

また ```group_vars/all``` をお好みで編集してください

__初期化__

```
ansible-playbook -i hosts/host init.yml  -vvvv -k
```
ユーザー作成やSSHのポート変更などをします。  
このスクリプトは1回のみ実施してください。  
(SSHのポート番号を変えるので冪等性を保証してません)  
最初にrootのパスワード(メールでくるパスワード)、  
次にログインユーザーのパスワード(自分が使いたいパスワード)が尋ねられます。  


__セットアップ__

```
ansible-playbook -i hosts/host setup.yml  -vvvv -k
```
サーバーの主なセットアップを行います。  
こちらは必要に応じて何度でも実行できます。  

