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

#### 撤销操作 
##### git commit --amend：有时候我们提交完了才发现漏掉了几个文件没有添加，或者提交信息写错了。 此时，可以运行带有 --amend 选项的提交命令来重新提交、



### .gitignore文件
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


