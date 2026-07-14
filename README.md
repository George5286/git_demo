# git语法

## cls，清空终端

```bash
cls
```

## 初始化

```bash
git config --global user.name "user_name"
git config --global user.email "email"
```

## clone github上的仓库

```bash
git clone 加上仓库网址
```

## 新建仓库时

- 新建文件夹
- 在文件夹中打开git
- 输入 `git init`（初始化）

## 提交到暂存区与仓库

```bash
git add+文件名
git add.
git commit -m "备注内容"
```

- `git add+文件名`（提交到暂存区）
- `git add.`（上传文件夹全部内容到暂存区）
- `git commit -m "备注内容"`（添加到仓库）

## 查看提交记录

```bash
git log
git log --stat
```

- `git log`（查看提交记录）
- `git log --stat`（每次提交修改了什么文件）

## 查看修改内容

```bash
git diff +commit id
```

- `git diff +commit id`（这一次提交修改了什么内容）

## 代码回溯

```bash
git reset -- hard commit id
git checkout commit id
```

- `git reset -- hard commit id`（代码回溯到旧版本，旧版本以后的版本全部删除）
- `git checkout commit id`（只移动了head指针并指向旧版本）

## branch（版本分支）

```bash
git branch
git branch +分支名
git checkout -b develop
git checkout main
git merge develop
```

- `git branch`（显示仓库有哪些分支）
- `git branch +分支名`（新建一个分支，但head指针不会切换到新分支而是保持不变）
- `git checkout -b develop`（创建了一个叫develop的分支且切到这个分支（head指针移到了新分支）（可以发布预览版在这个分支上））
- `git checkout main`（切换到main分支）
- `git merge develop`（将develop分支的代码合并到当前分区）

## 关于head指针

- head指针最终指向的commit可以理解为你所能看到的commit。
- 指针的关系：`head——>main(分支)——>commit的版本`
- 当新建了一个分支a，分支a会指向现在看到的commit版本，head指针不会动；当执行 `git checkout a` 指令，head会指向a分支，如果在此环境下修改代码上传到仓库，指针关系会变成 `head->a->新commit`，实现了并行开发，两个分支互不打扰。
- 如果使用 `git checkout commit id` 进行代码回溯，指针关系变成 `head->回溯的commit`，二没有分支这一步，在此境况下修改代码commit后，指针关系变成 `head->新commit`，原来回溯的commit依然留在main分支上，相当于新commit不属于任何一个分支，是很容易丢失的，所以我们要接着新建一个分支，指针变成 `head->新分支->新commit`。
