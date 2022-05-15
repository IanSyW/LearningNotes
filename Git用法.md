# Git

### 三种状态和工作模式

工作区

暂存区：stage

仓库：本地仓库

### 创建仓库并提交文件

- 创建仓库：git init

- git add 1.txt 提交到暂存区stage
- git commit -m “git版本库初始化”  # -m提交日志

``` linux
git init  # 初始化仓库
git status  # 查看工作区、暂存区状态
git add 1.txt  # 添加到stage暂存区
# git add .
git commit -m "备注信息"  # -m指添加日志
git log  # 查看提交日志信息

git config --list
```

### 版本回退

``` linux
# 撤销暂存区的所有文件
git reset HEAD 

# 简化输出
git log --pretty=oneline  # 在一行输出 !自动补全
git log -5  # 输出前五条
git log -5 --pretty=oneline

cat test01.txt  # 查看文档内容

# 版本回退
git reset --hard HEAD^^^  # 向上回退三个版本
git reset --hard HEAD~3

# 回到未来
git reset --hard 573b1  # 指定标识符

git reflog  # 查看所有改动日志
```

### 文件删除

``` linux
# 查看不一致的文件
git checkout

# 从本地仓库中恢复文件到工作区
git checkout -- test02.txt  
git checkout test02.txt 

# 彻底删除工作区和仓库中的文件
git rm test02.txt  # 可以通过reset回退

# 显示仓库中的所有文件
git ls-files  
```

### 远程仓库

> github     octotree
>
> 码云

git config --list

``` linux
# 远程到本地
git clone URL

# 本地到远程 HTTP
git remote add origin https://github.com/IanSyW/GitInit.git
git push -u origin master

# 本地到远程 SSH
1. ssh-keygen -t rsa -C "shiyiyang17@163.com"  # 生成公钥私钥，公钥复制到SSHKEY
2. ssh -T git@github.com  # ssh检测
3. git remote add origin git@github.com:IanSyW/GitInit.git
4. git push -u origin

git pull -rebase origin master  # 
```

