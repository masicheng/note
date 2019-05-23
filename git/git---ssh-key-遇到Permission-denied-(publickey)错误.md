 git clone 命令时报 Permission denied (publickey)错误，在官网[https://help.github.com/en/articles/checking-for-existing-ssh-keys](https://help.github.com/en/articles/checking-for-existing-ssh-keys)找到了解决方法

Mac版的解决方法(其它系统可在官网看到，大同小异)如下：

第一步： 检查电脑中是否存在ssh key

1.  打开命令终端输入**ls -al ~/.ssh**命令

2.  默认情况下会列出以下文件或之一：

*   id_dsa.pub

*   id_ecdsa.pub

*   id_ed25519.pub

*   id_rsa.pub

 这几个文件的内容是所需的ssh公钥，我在输入命令后只显示 known_hosts的存在，所以需要生产一个新的ssh key，如果有以下文件或之一，即可**跳过**第二步

第二步：生成一个新的ssh key

1.  在终端中输入**$ssh-keygen -t rsa -b 4096 -C "your_email@example"** 双引号里面是你的github账号邮箱

2.  会出现**> Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]**，

这里是可以输入一个文件名来保存sshkey，直接回车即可，回车后会提示输入两次密码，

> Enter passphrase (empty for no passphrase): [Type a passphrase]

> Enter same passphrase again: [Type passphrase again]

输入一个密码即可，密码作用具体参考[https://help.github.com/en/articles/working-with-ssh-key-passphrases](https://help.github.com/en/articles/working-with-ssh-key-passphrases)

第三步：将ssh key 添加进你的github账号

1.  找到.ssh目录下生成的文件，拷贝**.pub文件**里面的公钥

2.  添加过程可参考[https://help.github.com/en/articles/adding-a-new-ssh-key-to-your-github-account](https://help.github.com/en/articles/adding-a-new-ssh-key-to-your-github-account) 不再详述

添加完成后再试下git clone 命令就不会报Permission denied (publickey) 的错误了。
