# Atrantic Cloud VPS setup 
Atrantic Cloud VPSをセットアップするためのansibleスクリプトです


## 初期化
このスクリプトは1回のみ実施
(SSHのポート番号を変えるので冪等性を保証していない)

```
ansible-playbook -i hosts/host init.yml  -vvvv -k
```

## サーバーセットアップ
