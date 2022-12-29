# Github使用

## Github基础知识

- 在git中，开发者将源代码存入名叫”Git仓库“的资料库中并加以使用。而Github则是在网络上提供Git仓库的一个服务。
- Github上公开的软件源代码全都由Git进行管理。
- Github的Pull Request不但能轻松查看代码的前后差别，还可以对指定的一行代码进行讨论，使代码审查的工作变得前所未有的惬意。
- - 如果想让特定用户查看信息，可以用“@用户名”的格式书写，对方便会接到通知（Notification），查看Issue。
  - 输入”@组织名“，可以让属于该Organation（组织）的所有成员收到通知。
  - 输入”@团队名“可以让该团队的所有成员收到通知。
  - 输入“#编号”，会连接到该仓库所对应的Issue编号。
  - 输入“用户名/仓库名 # 编号”则可以连接到指定仓库所对应的Issue编号
  - 只需按照这类特定格式书写便会自动创建链接。
  - 只需将感兴趣的仓库添加到Watch中，就可以在News Feed查看该仓库的相关信息。也可以通过Pull Resquest提交代码。

### Issue

- Issue功能是将一个任务或问题分配给一个Issue进行追踪和管理的功能。
- 每一个功能更改或修正对应一个Issue，讨论或修正都以Issue为中心进行。只要查看Issue，就能知道和这个更改相关的一切信息，并以此进行管理。
- 在Git的提交信息中写上Issue的ID（例如：#7），Giothub就会自动生成从Issue到对应提交的链接。
- 只要按照特定的格式描述提交信息，还可以关闭Issue。

### Wiki

- 任何人都能通过Wiki对一篇文章进行更改和保存，该功能通常用在开发文档或手册的编写中。
- 改版的历史记录会被保存下来，且支持克隆至本地进行编译。

### Pull Request

- Pull Request送出后，目标仓库的管理人将能够查看Pull Request的内容及其中包含的代码更改。
- Pull Request和源代码前后差别均可以进行讨论。

## Git的导入

### 集中型与分散型

版本管理系统分为**Subversion**这类的集中型的与**Git**这类分散型的

#### ······ 集中型

- 该类型会将仓库集中存放在服务器之中，故只存在一个仓库。
- 集中型将所有数据集中存放在服务器中，有便于管理的优点。
- 一旦开发者所处的环境不能连接服务器，就无法获取最新的源代码，开发也无法进行。

#### ······ 分散型

- ​	GitHub将仓库Fork给每一个用户。
- - Fork就是将GitHub的某个特定仓库复制到自己的账户下。Fork出的仓库与原仓库是两个不同的仓库，开发者可以随意编辑。
- 分散型有多个仓库，本地的开发环境中就有仓库，开发者也可以本地开发。
- 所有仓库之间都可以进行push和pull

### Git Bash初始设置

#### 设置姓名和邮箱地址

``` Git bash
$git config --global use.name"Bregloomy16"
$git config --global user.email"user.email@example.com"
```

- 设置的姓名和邮箱地址会用在Git的提交日志中。
- 姓名和邮箱会随GitHub仓库一起公开，不要上传隐私信息。

#### 提高命令的可读性

- 更改命令颜色

``` Git Bash
$git config --global color.ui auto
```

## 使用GitHub的前期准备

### 使用前的准备

#### 设置SSH Key

- 运行下面的命令创建SSH Key

```Git Bash
$ssh-keygen -t rsa -C "your_email@example.com"
```

- 连按三次回车。

#### 添加公开密钥

- GitHub→Account Setting→SSH Keys→Add SSH key
- 在Title中输入合适的名称，key部分粘贴id_rsa.pub内容。
- 查看id_rsa.pub

```Git bash
$cat ~/.ssh/id_rsa.pub
```

- 测试

```Git Bash
ssh -T git@github.com
```

 ### 动手使用

#### 克隆库

``` Git Bash
$git clone git@github.com:用户名/仓库.git
```

#### 提交库

``` Git Bash
$git add 文件名
```

#### 上传库

``` Git Bash
$git push 
```

## 实际操作学习Git

### 基本操作

- git init——初始化仓库

  要使用Git进行版本管理，必须先初始化仓库。Git是使用git init命令进行初始化的,先实际建立一个目录并初始化仓库。

  ``` Git Bash
  $mkdir git-tutorial
  $cd git-tutorial
  $git init
  ```

  git中，该目录为“附属于该仓库的工作树”，文件编辑等操作在工作树中进行，然后记录到仓库中，以此管理文件的历史快照。

- git status——查看仓库的状态

- git add——向暂存区中添加文件

- git commit——保存仓库的历史记录

- - ······记述一行提交信息

  ```Git Bash
  $git commit -m "First commit"
  ```

  记述一行提交信息。

- - ······记述详细提交信息

  ```Git Bash
  $git commit
  ```

  编辑器中提交信息的格式：

  - - 第一行：用一行文字简述提交的更改内容。
    - 第二行：空行。
    - 第三行以后：记述更改的原因和详细内容。
  - - ”#“标为注释的`Change to be committed`栏中，可以查看本次提交中包含的文件。记述完毕后注意保存并退出编辑器。

- - ······中止提交

    将提交信息留空并直接关闭编辑器，随后提交就会中止。

- - ······查看提交后的状态

    ```Git Bash
    $git status
    ```

    

- git log——查看提交日志

  ```Git Bash
  $git log
  ```

  出现的内容中，commit后面的是提交的哈希值。

- - ·····只显示提交信息的第一行

  ```Git Bash
  $git log --preety=short
  ```

- - ······只显示指定目录、文件的日志

    `git log`命令后加上目录名，只会显示该目录下的日志。如果加的是文件名，只会显示与该文件相关的日志。

  - ······显示文件的改动

    `$git log -p 文件名`

  - ······git diff——查看更改前后的差别

    `$git diff 文件名`

- 建议养成在执行`git commit`命令前先执行`git diff HEAD`命令，以查看前后的区别

### 分支操作

- 在进行多个并行作业时，我们会用到分支。在这类并行开发的过程中，往往同时存在多个最新代码状态。

- 例如：在master分支创建feature-A和fix-B分支后，每个分支都有自己最新的代码。
- master分支是Git默认创建的分支，因此基本上所有的开发都是以这个分支为中心进行的。
- 不同的分支可以同时进行完全不同的作业，等该分支的作业完成之后再与master分支合并。

#### 相关命令

- git branch——显示分支一览表

- git checkout -b——创建、切换分支

- ······切换到feature-A分支并进行提交

  ```Git Bash
  $git checkout -b feature-A
  ```

  效果等同于：

  ```Git Bash
  $git branch feature-A
  $git checkout feature-A
  ```

  "*"所在位置，即为当前所在分支。不断对一个分支进行提交操作，称为“培育分支”。

  ```Git Bash
  $git add README.md
  $git commit -m "Add feature-A"
  ```

- ······ 切换到master分支

  ```Git Bash
  $git checkout master
  ```

  其他分支的更改无法影响主分支的内容。

- ······ 切换回上一个分支

  ```Git Bash
  $git checkout -
  ```

##### 各个分支功能作用

- master: 主分支，主要用来版本发布。
- develop：日常开发分支，该分支正常保存了开发的最新代码。
- feature：具体的功能开发分支，只与 develop 分支交互。
- release：release 分支可以认为是 master 分支的未测试版。比如说某一期的功能全部开发完成，那么就将 develop 分支合并到 release 分支，测试没有问题并且到了发布日期就合并到 master 分支，进行发布。
- hotfix：线上 bug 修复分支。

##### 特性分支

- Git创建分支不需要连接中央仓库，其创建的分支为“特性分支”。
- 特性分支：集中实现单一特性（主题），除此之外不进行任何作业的分支。
- 在日常开发中，往往会创建数个特性分支，除此之外在保留一个随时可以发布软件的稳定分支。
- 稳定分支一般由master分支担当。

##### 主干分支

- 主干分支是特性分支的原点，同时也是合并的终点。
- 一般把master分支作为主干分支。
- 主干分支并没有开发到一半的代码。

##### git merge——合并分支

首先切换到主干分支master。

```Git Bash
$git checkout master
```

合并feature-A分支时，为了在历史记录中明确记录下本次分支合并，需要创建并提交。在合并时加上`--no-ff`参数。

```Git Bash
$git merge --no-ff feature-A
```

默认信息中已经包含了从feature-A分支合并过来的相关内容，所以可以不做更改。

##### git log --graph——以图表的形式查看分支

`git log --graph`命令可以用图表的形式输出提交日志。

### 更改提交的操作

#### git reset——回溯历史版本

- Git可以灵活操作历史版本，借助分散仓库的优势，可以在不影响其他仓库的前提下对历史版本进行操作。
- 回溯可以将仓库的HEAD、暂存区、当前工作树回溯到指定的状态。

##### ······回溯到创建feature-A分支前

- 目标：回溯到feature-A分支创建之前，创建fix-B特性分支。

- 使用`git reset --hard 哈希值`命令，提供目标时间点的哈希值，可以完全恢复至该时间点的状态。

  - 创建fix-B分支。

    ```Git Bash
    $git checkout -b fix-B
    ```

##### ······推进至feature-A分支合并后的状态

- 该操作称为“推进历史”。
- `git log`只能查看以当前状态为终点的历史日志，所以要使用`git reflog`命令，查看当前仓库的操作日志。
- 在日志中找出回溯历史之前的哈希值，再通过`git reset --hard`命令恢复。
- 最后使用`git merge --no -ff fix-B`来合并分支。

##### ······ 查看冲突部分并将其解决

用编辑器打开README.md文件，修改成

```Git Bash
- feature-A
- fix-B
```

在处理冲突时，务必仔细分析冲突部分的内容后再修改。

##### ······提交解决后的结果

```Git Bash
$git add README.md
$git commit -m "Fix conflict"
```

#### git commit -amend——修改提交信息

```Git Bash
$git commit -amend
```

##### git rebase -i ——压缩历史

- 如果发现已提交的内容中有些拼写错误等，不妨提交一个修改，然后将这个修改包含到前一个提交之中，压缩成一个历史记录。

- ······· 创建feature-C分支

- - 作为feature-C的功能实现，在README.md文件中添加一行文字，并留下拼写错误等待修正。
  - 使用`git commit -am`命令来完成`git add`和`git commit`两个命令的作用。

- ······ 修正拼写错误

  自行修正README.md的拼写错误，用`git diff`查看修改后的差别。

  ``` Git Bash
  $git diff
  ```

  然后提交信息

  ```Git Bash
  $git commit -am "Fix typo"
  ```

  错字漏字等失误称作typo。

- ······ 更改历史

  ```Git Bash
  $git rebase -i HEAD-2
  ```

  执行`git rebase`命令，可以选定当前分支中包含HEAD（最新提交）在内的两个最新历史记录为对象，并在编辑器中打开。

  例：

  ```Git Bash
  pick 7a34294 Add feature-C
  pick 6fba227 Fix typo
  ```

  修改为：

  ``` Git Bash
  pick 7a34294 Add feature-C
  fixup 6fba227 Fix typo
  ```

  系统显示rebase成功。也就是以下面这两个提交作为对象，将“Fix typo”的内容合并到了上一个提交“Add feature-C”中，改写成了一个新的提交。

- ······合并至master分支

- ```Git Bash
  $git checkout master
  $git merge --no-ff feature-C
  ```

### 推送至远程仓库

- 在GitHub上新建仓库时，为了与本地仓库保持一致，不要勾选`Initialize this repository with a README`选项，会失去与本地仓库的整合性。

- git remote add——推送至远程仓库

  ```Git Bash
  $git remote add origin git@github.com:用户名/仓库名.git
  ```

- git push ——推送至远程仓库

- - ······推送至master分支

  ```Git Bash
  $git push -u origin master 
  ```

  -u参数可以在推送时，将origin仓库的master分支设置为本地仓库当前分支的上游。添加了这个参数。将来运行`git pull`命令从远程仓库获取内容时，本地仓库的这个分支就可以直接从origin的master分支获取内容。

- - ······ 推送至master以外的分支

  例：推送至feature-D分支

  ```Git Bash
  $git checkout -b feature-D
  $git push -u origin feature-D
  ```

  ### 从远程仓库获取

  在另一个目录下新建一个本地仓库，学习从远程仓库获取内容。

- ······ 获取远程仓库

  换到我们换到其他目录下，将Github上的仓库clone到本地。

  ```Git Bash
  $git clone git@github.com:用户名/仓库名.git
  $cd 仓库名
  ```

- 执行`git clone`命令后，默认处于master分支下，同时系统自动会将origin设置成该远程仓库的标识符。

  当前的本地仓库使用的master分支与GitHub端远程仓库（origin）的master分支在内容上是相同的。

  ```Git Bash
  $git branch -a
  ```

  用`git branch -a`命令查看当前分支的相关信息，添加-a参数可以同时显示本地仓库和远程仓库的分支信息。

- ······获取远程的feature-D分支

  ```Git Bash
  $git checkout -b feature-D origin/feature-D
  ```

  例子中指定了origin/feature-D，以名为origin的仓库（这里指GitHub端的仓库）的feature-D分支为来源，在本地仓库创建feature-D分支。

- ······ 向本地的feature-D分支提交更改

   ```Git Bash
  $git diff
  ```

  按照之前学过的方式提交：

  ```Git Bash
  $git commit -am "Add feature-D"
  ```

- ······ 推送feature-D分支

  ```Git Bash
  $git push
  ```

  从远程仓库获取feature-D分支，在本地仓库中提交更改，再将feature-D分支推送回远程仓库。

#### git pull——获取最新的远程仓库分支

```Git Bash
 $git pull origin feature-D
```



