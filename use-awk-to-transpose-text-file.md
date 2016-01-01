title: Use Awk to transpose text file
date: 2013-06-28 22:42:59
category: Tools
tags:
---

<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#orgheadline1">1. 前话</a></li>
<li><a href="#orgheadline3">2. 正文</a>
<ul>
<li><a href="#orgheadline2">2.1. 脚本conv.awk</a></li>
</ul>
</li>
</ul>
</div>
</div>


# 前话<a id="orgheadline1"></a>

这段时间在做一些性能测试实验，经常使用bash，sed，awk 对实验结果做一
些自动化的分析。这样就顺便学了一把bash awk什么的。空间的时候就想了一
个使用awk对文本内容进行行列互换的脚本。

# 正文<a id="orgheadline3"></a>

比如现在有文件test.txt内容为：

    11    12      13      14
    21    22      23      24
    31    32      33      34

使用awk脚本转换后的内容则为：

    11    21      31
    12    22      32
    13    23      33
    14    24      34

## 脚本conv.awk<a id="orgheadline2"></a>

    #!/usr/bin/awk -f
    
    BEGIN {
      lines=0
      cols=0
    }
    
    {
      if (NF > cols)
        cols=NF
      lines++
      for (i=1; i<=NF; i++)
        data[NR, i]=$i
    }
    
    END {
      for (i=1; i<=cols; i++) {
        for (j=1; j<=lines; j++)
          printf data[j,1]"\t"
        printf "\n"
      }
    }
