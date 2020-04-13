# 如何在一台电脑上同时连接gitlab与github仓库

1. 生成gitlab与github对应的ssh key
`ssk-keygen -t rsa -C "your.email@example.com"`
注意执行完上一步代码的时候，生成的密钥文件的文件名一定要区分开。

2. 进入目录查看生成的公钥和私钥
`cs ~/.ssh`

3. 修改config配置
`vim config`

# gitlab
Host gitlab
    User git
    HostName gitlab.cheanjiait.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa

# github
Host github
    User git
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa_github

4. 创建一个目录，供gitlab使用

`mkdir fe_project`
`cd fe_project`
`git config --local user.name 'zty'`
`git config --local user.emial 'your@qq.com'`

直接拉取代码，如果不可以，就把私钥加入队列
`git-add ~/.ssh/github_id_rsa`
然后再拉取代码