


# Vagrant Boxのダウンロード

#### Boxを探す
[chef/bento](https://github.com/chef/bento)
- Chef社でメンテされているboxが置いてある
- `Chef Client`は入ってないので注意

#### ダウンロード
```bash
vagrant add box ${url}

# example
vagrant box add opscode-centos-6.6 http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-6.6_chef-provisionerless.box
```
- ダウンロードしたboxは、`~/.vagrant.d`に保存されている

####
# Reference
