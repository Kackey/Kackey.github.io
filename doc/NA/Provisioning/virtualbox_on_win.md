
# SSH
WindowsではSSHが入っていないので、
`vagrant ssh`でエラメッセージが表示される。
```bash
>vagrant ssh
`ssh` executable not found in any directories in the %PATH% variable. Is an
SSH client installed? Try installing Cygwin, MinGW or Git, all of which
contain an SSH client. Or use your favorite SSH client with the following
authentication information shown below:

Host: 127.0.0.1
Port: 2200
Username: vagrant
Private key: C:/Users/hidekazu.kakinuma/.vagrant.d/insecure_private_key

```

Git for Windowsのsshを利用できるようにしておく

[Git for Windows](http://msysgit.github.io/)

インストールのウィザードで、必ず
"Adusting your PATH environment."のところで
`Run Git from the Windows Command Prompt`を選んでおく
（でないと、Git Bash上でしかsshを使えない）

コマンドプロンプトでsshの実行を確認
↓と表示されればOK
```bash
$ ssh
usage: ssh [-1246AaCfgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-E log_file] [-e escape_char]
           [-F configfile] [-I pkcs11] [-i identity_file]
           [-L [bind_address:]port:host:hostport] [-l login_name] [-m mac_spec]
           [-O ctl_cmd] [-o option] [-p port]
           [-Q cipher | cipher-auth | mac | kex | key]
           [-R [bind_address:]port:host:hostport] [-S ctl_path] [-W host:port]
           [-w local_tun[:remote_tun]] [user@]hostname [command]
```
「コマンドが見つかりません」的なことを言われる場合は、
PATHをチェックして`${Gitのインストールディレクトリ}\Git\bin`にPATHを通しておく
```bash
ex) C:\Program Files (x86)\Git\bin
```

# Reference
###### WindowsでSSHを使うための設定
- [今すぐVagrantを始めよう | 株式会社シンメトリック公式ブログ |](http://www.symmetric.co.jp/blog/archives/533)

- [WindowsにおけるGit利用環境は整った： Git for Windows と SourceTree for Windows - 檜山正幸のキマイラ飼育記](http://d.hatena.ne.jp/m-hiyama/20140203/1391381365)
  - SSH利用を想定した`Git for Windows`のインストール方法

###### Vagrant上でのiptables設定、
- [WindowsでVagrantの環境構築 - Qiita](http://qiita.com/yoh-nak/items/95c735764f38c37ea16a)
  - 仮想マシン上でのiptables設定（ファイヤーウォールの無効化）
  - Win上ターミナルの設定例(Pedorosa)
  - 共有フォルダ上へのシンボリック作成例（Webサーバのドキュメントルート）
