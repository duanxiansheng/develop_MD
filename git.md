- 每次上传都要先pull一下，这样防止报错
- git rm ./src/..    删除本地仓库文件，然后push可以删除远程的文件
- git全局设置

- - 用户名  git config --global user.name "姓名英文"

  - 邮箱   git config --global user.email "真实邮箱"

  - - git config --list 查询全局配置列表 看是否是自己的邮箱或用户名，如果没有就没配置上

- 新建项目-安装git软件

- - 仓库名称为英文
  - 私有收费，公开免费
  - 不使用任何方法去初始化仓库

- 关联本地git仓库于github仓库

- - 手动建立密钥建立密匙

  - - ssh-keygen -t rsa -C "1004387497@qq.com"   //三次回车生成

    - - 结果就可以看到一个C盘的地址 c/用户/D/ssh

- - - - 找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥

- - 在GitHub中添加秘钥	

- - - 登录GitHub 个人设置 /Settings

    - 左边SSH和GPG/SSH and GPG keys

    - 添加新的秘钥/SSH密钥

    - 在标题/title里起名

    - 在键/key里粘贴id_rsa.pub文件的内容，id_rsa.pub在c盘用户里

    - 测试ssh key是否成功

    - - 命令“ssh -T git@github.com”
      - 如果出现 You’ve successfully authenticated, but GitHub does not provide shell access 
      - 这就表示已成功连上github。

- 打开id_rsa记事本-复制代码到gitee官网左边“ssh公钥”-标题为存储名字

- ssh -T git@gitee.com 查询是否接通码云 或者  ssh -T git@github.com查看是否接通github

- - 第一次绑定，弹出信息是是否继续接通，选择yes

- git init

- - 第一次上传需要初始化仓库，这样就有.git隐藏文件夹了

- git remote add origin https: //自己的仓库url地址

- - 将本地的仓库关联到git上，HTTPS 地址,绑定远程仓库，GitHub也是这样

- git add ./       或者        git add ./某个文件

- - ./ 所有文件         

- git commit -m ‘添加注释

- git push 

- - 上传到远程仓库中

  - git push ssh地址

  - 错误

  - -   git push --set-upstream origin master //本地的分支没有和远程分支建立联系

    - - git push --set-upstream origin master（master可以根据子的需要自定义，就是当前分支在远程分支对应的名称）

- git pull 

- - 拉取远程仓库与本地分支合并

  - git clone -b develop git@gitee.com:weber_D/demo.git   // 拉取别的分支下的文件

  - - 其中develop就是分支的名称

- 新建文件夹下拉取

- - git clone ssh地址

- 分支

- - 在本地查询不到分支,在gitee上创建了新分支

  - - 
    - git fetch更新远程分支  或者 git push -u origin master 
    - git branch -a 查看
    - 第一次查询分支需要先上传远程才有本地分支

  -  git checkout -b [dev](https://www.baidu.com/s?wd=dev&tn=44039180_cpr&fenlei=mv6quAkxTZn0IZRqIHckPjm4nH00T1YLmWm1nW9hn1I-m1R3nWDd0ZwV5Hcvrjm3rH6sPfKWUMw85HfYnjn4nH6sgvPsT6KdThsqpZwYTjCEQLGCpyw9Uz4Bmy-bIi4WUvYETgN-TLwGUv3EnWmYnjTkPHfkn1n4nHckPWfd) origin/[dev](https://www.baidu.com/s?wd=dev&tn=44039180_cpr&fenlei=mv6quAkxTZn0IZRqIHckPjm4nH00T1YLmWm1nW9hn1I-m1R3nWDd0ZwV5Hcvrjm3rH6sPfKWUMw85HfYnjn4nH6sgvPsT6KdThsqpZwYTjCEQLGCpyw9Uz4Bmy-bIi4WUvYETgN-TLwGUv3EnWmYnjTkPHfkn1n4nHckPWfd)

  - - 作用是checkout远程的dev分支，在本地起名为dev分支，并切换到本地的dev分支
    - git branch -vv查看

  - git branch -a

  - - 查看分支,红色是远程，白色是本地

  - git checkout 分支名

  - - 切换分支

  - git branch dev

  - - 创建分支，创建了一个dev分支

  - 合并分支（远程分支）

  - - 先clone master 分支

    - -   git clone https://gitee.com/zhanghan_123/gittest.git

    - 创建本地dev分支与远程dev分支对应

    - -  git checkout -b dev origin/dev
      - 前提是本地没有dev分支， branch -vv查看是否对应上了

    - 切换master分支

    - - git checkout master

    - 将本地的dev合并到master上， 合并本地分支

    - - git merge dev   
      - 输入“：wq”，注意是英文输入状态下的冒号，然后按下“Enter”键即可。

    - 推送到远程master上

    - -  git push origin master   

  - git branch -vv

  - - 查看本地和远程分支是否一样

  - git branch -D dev 删除本地分支 前提要切换到别的分支

- 过滤文件

- - touch .gitignore //在gitbash输入 那集目录在哪创建成功

  - - 在项目中新建一个.gitignore 文件 增加需要排除的文件或目录,

- - - *.class *.apk  bin/  gen/  .settings/  proguard/

- 错误

- - 请在合并之前提交或隐藏更改。拉去分支有些拉去不下来。// 会保留自己更改拉去别的文件

  - - git stash     git pull    git stash pop  
    - git stash的时候会把你本地快照，然后git pull 就不会阻止你了，pull完之后这时你的代码并没有保留你的修改。惊了！ 别急，我们之前好像做了什么？
    - 这时候执行git stash pop你去本地看会发现发生冲突的本地修改还在，这时候你该commit push啥的就悉听尊便了。

  - //不保留自己更改 远程拉去覆盖

  - - git reset --hard            git pull 

- git status 查看状态

- 版本回退

- - 查看日志 git log

  - -  查看历史提交的日志，复制commit后面的ID 输入q退出 

  - 回退到指定的版本

  - - git reset --hard commit的ID

------

HTTPS地址远程上传

复制页面中的HTTPS地址，在git命令行输入 git push [地址] master

复制页面中的HTTPS地址，在git命令行输入 git push -u origin master

示例: git push https://github.com/huoqishi/test112.git master master

------

ssh地址上传(一般企业都用这种)

复制页面中ssh的地址，在git命令行输入 git push [地址] master 

yes

------