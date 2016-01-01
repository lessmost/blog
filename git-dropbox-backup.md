title: 私有git代码的备份
date: 2012-03-20 14:42:59
category: Tools
tags: Git
---

# 私有git代码的备份

私有git代码托管在[bitbucket](https://bitbucket.org)上非常的方便，但自己还是要备份下的。Git的
hook就可以用来自动备份代码了。

在project目录下的新建文件 ~.git/hooks/post-commit

    #!/bin/sh
    
    project_name=${PWD##*/}
    git bundle create ~/data/Dropbox/repo/${project_name}.bundle \
        --all --tags --branches

然后chmod +x .git/hooks/post-commit。

这样，在commit后就会自动的创建git bundle到指定的目录了。
