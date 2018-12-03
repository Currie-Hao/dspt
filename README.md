# dspt
#四种基本配置，照抄就行：
##1.配置用户名：git config --globl user.name "你的用户名（随便起）"
##2.配置邮箱： git config --globl user.email"你的邮箱"
##3.避免git中的中文乱码：git config --global gui.encoding utf-8
##4.避免git显示的中文文件名乱码： git config --global core.quotepath.off
#git ssh key pair配置
##1.git bash中设置：ssh-keygen -t rsa -C "你的邮箱"
##2.一路回车，没有其他操作
##3.在用户目录下生成.ssh文件夹，找到公钥和私钥
##（id_rsa id_rsa.pub）
##4.将公钥的内容复制，进入github网站，将公钥添加进去
#
#
#git常用命令：
 ###git init 常见本地仓库
 ###git add 添加到暂存区
 ###git commit -m "描述" 提交到本地仓库
 ###git status 检查工作区文件状态
 ###git log 查看提交committid 
 ###git reset --hard committid 版本回退
 ###git branch 查看分支
 ###git checkout -b dev 创建并切换到dev分支
 ###git checkout 分支名  切换分支
 ###git pull 拉取
 ###git push -u origin master 提交到远程仓库（以后提交仓库不用写-u）
 ###git merge 另一个分支名  合并分支