ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDsOg9b2Gqz6di0IPFe85LkXCiS+GHrytiLLP++jkFE9M+JUrgWobSD6ujhw2fnQOydjmxRLLu+mSpdJJpxp3o/H/K/B6a2oTZeBB2NhUyIe3vSfHgj6y5nxGgiE9PqzByyvinbmWgxQjYFr1OIbEZdtGgDJtQIRLvtQW9qOdDrVFW2sLXAp+4Kx8/vWvgmzhu+SO8fQGawgayRX0lCX18aQ+a8ClL6Pv0QCP8W9s9MMEzAePG1dOfQ7MRyyV74UcKXJCUzMrJ5Z7bO92RSTJ1mklGVdWgkmks3vyXtauAuFGwglOwnWsEwPrYmJGv4ud1lJLp2vxxvxJPXaMit3qiPvqXIA41w2SGtC7nK1tHf4tPFZqKhhqp6rAe+2vrEIgUvYIQRuD5EC2LVkKEal8y9A8465CW6N3Ef+ai6ZBkbEwKgsYfe/B0NVS1yTcLfMaOZ9kfaUrKyLPqZ+Hp2f8R2VEb5fCp4hFmwwpoM51+8BJfadI2V3sfpl7cN5KrKXdU= ecpknjh@buaa.edu.cn


1.在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，创建SSH Key，ssh-keygen -t rsa -C "youremail@example.com"
这样以后，可以在.ssh目录里面找到id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。
2.登陆GitHub，打开“Account settings”，“SSH Keys”页面，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容,点“Add Key”

情景是，你已经在本地创建了一个Git仓库后，又想在GitHub创建一个Git仓库，并且让这两个仓库进行远程同步
登陆GitHub，然后，在右上角找到“Create a new repo”按钮，创建一个新的仓库
在Repository name填入learngit，其他保持默认设置，点击“Create repository”按钮，就成功地创建了一个新的Git仓库
可以从这个仓库克隆出新的仓库，也可以把一个已有的本地仓库与之关联，然后，把本地仓库的内容推送到GitHub仓库。
在本地对应的文件夹下运行命令：git remote add origin git@github.com:michaelliao/learngit.git,在本地关联远程库,添加后远程库的名字就是origin
下一步，就可以把本地库的所有内容推送到远程库上：把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程。
由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
推送成功后，可以立刻在GitHub页面中看到远程库的内容已经和本地一模一样
从现在起，只要本地作了提交，就可以通过命令：

$ git push origin master

把本地master分支的最新修改推送至GitHub
删除远程库
如果添加的时候地址写错了，或者就是想删除远程库，可以用git remote rm <name>命令。使用前，建议先用git remote -v查看远程库信息
然后，根据名字删除，比如删除origin：
$ git remote rm origin
此处的“删除”其实是解除了本地和远程的绑定关系，并不是物理上删除了远程库。远程库本身并没有任何改动。要真正删除远程库，需要登录到GitHub，在后台页面找到删除按钮再删除。