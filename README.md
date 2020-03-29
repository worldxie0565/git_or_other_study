# git_study
这是一个git相关的一些知识点,用于git的学习    

## 使用git将本地仓库push到远程仓库上（包括readme.md）      
1. 在本地项目目录文件下右键鼠标点击git bash here，使用git init命令初始化一个新的仓库   
2. 在github上面新建一个项目（不初始化readme.md，最后我们会处理它）
3. git remote add origin + 远程仓库url
4. git add .
   git commit -m “说明”
   git push -u origin master
5. 此时，刷新github上面的内容，发现已经提交到远程仓库上面了。
6. 在github下面有一个create readme.md选项（如果你项目中没有readme.md的话），创建并编辑。
7. 使用git pull origin master:master命令，将远程仓库上面的内容pull到本地仓库（因为此时远程仓库比本地仓库多一个readmd.md）
8. 大功告成，给自己鼓掌，切记以后尽量不要再github上面直接编辑文件，需要在本地仓库改变文件后进行第4步即可。
9. 若不小心在github上面动了代码也不要紧，使用第7步即可。
