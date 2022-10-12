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

- 先按回车键，再输入密码。
- 请选择复杂度高且容易记忆的组合。

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

  