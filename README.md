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
- develop —— 开发人员的基础分支，所有的开发功能分支（feature）都**必须**从 develop 分支上进行拉取，同时也要合并到 develop 分支。



### 短期分支

- hotfixes —— 紧急分支，用于修改 master 分支上的错误，修改后**必须**将此分支合并到 master 和 develop 分支
- feature —— 功能分支，功能分支**必须**从 dev 分支切出，完成后提交 pr，review 后**必须**合并到 develop
- fix —— bug 修复分支，用与修改非生产环境出现的bug





### 分支规范

towerid 是**必须**存在的，如果不存在请联系项目组长

#### feature分支

feature 分支命名**必须**遵循 feature-{yourname}/{featurename}#{towerid}

#### hotfixes分支

hotfixes 分支命名**必须**遵循 hotfix-{yourname}/{hotfixname}#{towerid}

#### fix分支

fix 分支命名**必须**遵循 fix-{yourname}/{fixname}#{towerid}



# pull request

- pr **必须**提交到dev分支，**必须**组长或项目管理人员进行review后没有问题进行合并
- pr 遇到冲突时，**必须**自己解决。
- pr **应该**简述功能信息



# merge

- dev 分支

  代码通过提交 pr（同时写明信息）后，**必须**有至少一个人进行 review，review 后没有问题可以合并到 dev 分支

- hotfix 分支

  代码应从 master 分支切出，修改完成后**必须**提交两个 pr 分别到 master 和 develop，在 reviewer 审查没问题后合并到 master 和 develop

- fix 分支

  代码**必须**从 develop 分支切出，在修改完成后**必须**提交 pr（同时写明信息）后，在 reviewer 审查没问题后合并到dev

- feature 分支

  代码**必须**从 develop 分支切出，在功能完成后**必须**提交 pr（同时写明信息）后，在 reviewer 审查没问题后合并到develop

  


# tag

格式：vx.y.z，如 v1.0.0。其中x代表主版本号，y 代表次版本号，z 代表补丁号

如果只修改了 bu g则对 z 进行加一；

新增功能，向下兼容，没有删除功能对y进行加一；

不向下兼容，删除功能对x进行加一；

- master 分支

  master 分支在每次更新生产环境时**必须**打 tag，同时也可以标注出基本信息。
	
	



# 注意事项

- **不应该**直接提交代码到 master，develop 分支
- **必须**有一个 reviewer。
- 合并到 master 和 develop **必须**由 reviewer 进行。
- 除 master，develop 分支，其他所有分支应在使用完成后**必须**进行销毁删除。



## 其他

composer.lock 提交

composer.json 提交





package.lock 提交

package.json 提交

yarn.lock 提交



