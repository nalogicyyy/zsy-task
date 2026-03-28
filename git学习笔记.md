### 一、提交文件
**git init**
作用：把当前文件夹变成 git 仓库（第一次用）
**git add .**
作用：添加所有文件到暂存区（必须加空格）
**git commit -m "提交说明"**
作用：把文件提交到本地仓库
**git remote add origin 仓库地址**
作用：关联远程仓库（第一次用）
**git push -u origin main**
作用：把文件推送到远程仓库
### 二、删除已提交文件
**git rm --cached 文件名**
作用：只删除远程文件，保留本地文件
**git rm 文件名**
作用：同时删除远程和本地文件
**git rm -r --cached 文件夹名**
作用：只删除远程文件夹，保留本地
**git rm -r 文件夹名**
作用：同时删除远程和本地文件夹
**git commit -m "删除文件"**
作用：提交删除操作
**git push origin main**
作用：把删除操作同步到远程仓库