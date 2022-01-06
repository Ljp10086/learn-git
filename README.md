### 学习Git指令

##### git status：查看文件处于什么状态

参数：
1. s(short)：输出status的简短版本.

##### git diff：查看文件处于什么状态
参数：
1. staged：对比已暂存的文件与最后一次提交的文件差异。
2. cached：查看已经暂存的变化。

##### git commit：提交更新
该命令将默认打开vim编辑器，默认的提交消息包含最后一次运行 git status 的输出，放在注释行里，另外开头还有一个空行，供你输入提交说明。
参数：
1. m：将提交信息与命令放到同一行。

##### git rm <file>：删除文件，并且将缓存区中的该文件一并删除
手动删除一个缓存区的文件时可以直接使用rm。
参数：
1. f：删除缓存区与磁盘中的文件
2. cached：仅从暂存区删除
3. r：递归删除(文件夹)
##### git add <file>：暂存文件
##### git log：查看提交历史
参数：
1. p：查看提交差异
2. --stat：查看简短信息

#### tag

##### git tag：打标签
参数：
1. -l(--list)：这个命令以字母顺序列出标签，但是它们显示的顺序并不重要。

###### 删除标签：
本地：```git tag -d <tagName>```
远程：
1. ```git push <remote> :refs/tags/<tagName>```
2. ```git push --delete <tagName>```
   


###### 附注标签：
在运行```tag```命令时指定```-a```选项。
-m 选项指定了一条将会存储在标签中的信息。 如果没有为附注标签指定一条信息，Git 会启动编辑器要求你输入信息。
```
$ git tag -a v1.4 -m "my version 1.4"
$ git tag
v0.1
v1.3
v1.4
```

###### 轻量标签：
另一种给提交打标签的方式是使用轻量标签。 轻量标签本质上是将提交校验和存储到一个文件中——没有保存任何其他信息。
```
$ git tag v1.4-lw
$ git tag
v0.1
v1.3
v1.4
v1.4-lw
v1.5
```

###### 推送某个标签：```git push origin <tagname>```
###### 推送所有标签到远程仓库：```git push origin --tags```



#### 远程仓库
##### git remote：查看已经配置的远程仓库
参数：
1. -v：显示需要读写远程仓库使用的 Git 保存的简写与其对应的 URL。
2. add <shortname> <url>：添加一个新的远程仓库

##### git fetch <remote>：这个命令会访问远程仓库，从中拉取所有你还没有的数据。
不会自动合并代码。

#### 撤销操作 
##### git commit --amend：
有时候我们提交完了才发现漏掉了几个文件没有添加，或者提交信息写错了。 此时，可以运行带有 --amend 选项的提交命令来重新提交、
配合```-m```参数可以重新生成提交信息


#### 分支
##### 创建分支：```git branch testing```
##### 删除分支：```git branch -d testing```
##### 切换分支：```git checkout testing```
##### 新建同时切换分支：```git checkout -b testing```
带有```-b```参数的```git checkout```命令是以下两条命令的简写
```
git branch testing
git checkout testing
```
##### 合并分支：```git merge testing```

#### .gitignore文件
```
*.[oa]
*~
```

第一行告诉 Git 忽略所有以 .o 或 .a 结尾的文件。
第二行告诉 Git 忽略所有名字以波浪符（~）结尾的文件。


##### .gitignore 的格式规范如下：

1. 所有空行或者以 # 开头的行都会被 Git 忽略。

2. 可以使用标准的 glob 模式匹配，它会递归地应用在整个工作区中。

3. 匹配模式可以以（/）开头防止递归。

4. 匹配模式可以以（/）结尾指定目录。

5. 要忽略指定模式以外的文件或目录，可以在模式前加上叹号（!）取反。

```
# 忽略所有末尾为 .a 文件
*.a

# 跟踪所有的 lib.a，即便你在前面忽略了 .a 文件
!lib.a

# 只忽略当前目录下的 TODO 文件，而不忽略 subdir/TODO
/TODO

# 忽略任何目录下名为 build 的文件夹
build/

# 忽略 doc/notes.txt，但不忽略 doc/server/arch.txt
doc/*.txt

# 忽略 doc/ 目录及其所有子目录下的 .pdf 文件
doc/**/*.pdf
```


