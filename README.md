# Atrantic Cloud VPS setup 
Atrantic Cloud VPSをセットアップするためのansibleスクリプトです。
サーバーを契約した後rootで直接ログインせずに初期のセットアップを行えます。


## やること
 * SSHのポート変更
 * ログインユーザー作成
 * 鍵交換
 * タイムゾーン変更
 * レポジトリ更新
 * fail2banインストール(攻撃対策)

## 使い方

__Ansibleインストール__
前準備としてローカルにAnsibleをインストールしておいてください。

__設定の編集__

```hosts/host``` ファイルに対象サーバーのIPを追記してください。  
複数サーバーでも可能です。

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
ansible-playbook -i hosts/host setup.yml  -vvvv
```
サーバーの主なセットアップを行います。  
こちらは必要に応じて何度でも実行できます。  

必要な構成に応じてroleを追加して実行してください。


## 動作確認サーバー

* Atlantic Cloud: ubuntu-14.04_64bit Server

未確認ですが、Ubuntuでrootが取れるサーバーであればAtranticのVPSでなくても動くかと。
