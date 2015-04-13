
#### ディストリビューションとバージョンの確認

とりあえず↓を叩いてみるのが早い

```bash
cat /etc/issue
```

なければ、`/etc`配下にバージョンを記載したファイルが置いてあるので、これをチェックする。

```bash
/etc/redhat-release   # Redhat / CentOS
/etc/debian_version   # Debian
/etc/fedora-release   # Fedora
```
- CentOSだけ接尾辞が`_version`


```bash
$ cat /etc/redhat_release
```

#### カーネル情報
カーネルバージョン
```bash
uname -r
```

32bit or 64bit
```bash
uname -a
```
- **64bit:** `x86_64`,`amd64`
- **32bit:** `i686`, `i386`
