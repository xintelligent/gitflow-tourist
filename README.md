---
title: git规范
date: 2019-11-29 08:50:04
updated: 2019-12-02 17:07:59
author: 苗高鹏，宋建
tags: git
---

## 导读

> 为了避免歧义，文档大量使用了「能愿动词」，对应的解释如下：
>
> - **必须**（Must） - 只能这样子做，请无条件遵循，没有别的选项；
> - **绝不**（Must Not）- 严令禁止，在任何情况下都不能这样做；
> - **应该**（Should） - 强烈建议这样做，但是不强求；
> - **不应该**（Should Not） - 强烈建议不这样做，但是不强求；
> - **可以**（May） - 选择性高一点
>
> 参考：[RFC 2119](https://www.ietf.org/rfc/rfc2119.txt)



## 分支

### 长期分支

- master —— 主分支，同时也是线上最新代码的分支。
- develop —— 开发人员的基础分支，所有的开发功能分支（feat）都**必须**从 develop 分支上进行拉取，同时也要合并到 develop 分支。



### 短期分支

- hotfixes —— 紧急分支，用于修改 master 分支上的错误，修改后**必须**将此分支合并到 master 和 dev 分支。
- feature —— 功能分支，功能分支**必须**从 dev 分支切出，完成后提交 pr，review 后**必须**合并到 dev。
- fix —— bug 修复分支，用与修改非生产环境出现的bug。





### 分支规范

towerid是**必须**存在的，如果不存在请联系项目组长等。

#### feature分支

feature分支命名**必须**遵循feature-{yourname}/{featurename}#{towerid}

#### hotfixes分支

hotfixes分支命名**必须**遵循hotfix-{yourname}/{hotfixname}#{towerid}。

#### fix分支

fix分支命名**必须**遵循fix-{yourname}/{fixname}#{towerid}。



# pull request

- pr**必须**提交到dev分支，**必须**组长或项目管理人员进行review后没有问题进行合并。
- pr遇到冲突时，**必须**自己解决。
- pr**应该**简述功能信息。



# merge

- dev分支

  代码通过提交pr（同时写明信息）后，**必须**有至少一个人进行review，review后没有问题可以合并到dev分支。

- hotfix分支

  代码应从master分支切出，修改完成后**必须**提交两个pr分别到master和dev，在reviewer审查没问题后合并到master和dev。

- fix分支

  代码**必须**从dev分支切出，在修改完成后**必须**提交pr（同时写明信息）后，在reviewer审查没问题后合并到dev。

- feature分支

  代码**必须**从dev分支切出，在功能完成后**必须**提交pr（同时写明信息）后，在reviewer审查没问题后合并到dev。

  


# tag

格式：vx.y.z，如v1.0.0。其中x代表主版本号，y代表次版本号，z代表补丁号

如果只修改了bug则对z进行加一；

新增功能，向下兼容，没有删除功能对y进行加一；

不向下兼容，删除功能对x进行加一；

- master分支

  master分支在每次更新生产环境时**必须**打tag，同时也可以标注出基本信息。
	
	



# 注意事项

- **不应该**直接提交代码到master，dev，test分支。
- **必须**有一个reviewer。
- 合并到master和test**必须**由reviewer进行。
- 除master，dev，pre-releases分支，其他所有分支应在使用完成后**必须**进行销毁删除。



## 其他

composer.lock 提交

composer.json 提交

.gitignore 提交

