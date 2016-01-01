title: 我的 Openbox 窗口管理器的配置
date: 2013-06-28 22:47:41
category: Desktop
tags: Desktop
---

<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#orgheadline1">1. 前话</a></li>
<li><a href="#orgheadline2">2. 窗口的移动</a></li>
<li><a href="#orgheadline3">3. 窗口的拉伸</a></li>
<li><a href="#orgheadline4">4. 窗口的其他操作</a></li>
<li><a href="#orgheadline5">5. 程序启动快捷键</a></li>
</ul>
</div>
</div>


# 前话<a id="orgheadline1"></a>

在折腾了Gnome, KDE, XFCE, LXDE后，现在还是用着LXDE, 其实主要原因是
LXDE使用Openbox作为它的WM，和LXDE的简单。

Openbox的高度可配置性比GDM，KDM都好些，对窗口的管理更有力一些，当然
如果你是最大化流，这个就没多大意义了。

# 窗口的移动<a id="orgheadline2"></a>

首先我喜欢的配置就是对新建窗口的移动，如将窗口移动到屏幕中央，移动到
屏幕左，右，上，下侧：

    <keybind key="W-c">
      <action name="MoveToCenter"/>
    </keybind>
    <keybind key="W-w">
      <action name="MoveToEdge">
        <direction>north</direction>
      </action>
    </keybind>
    <keybind key="W-s">
      <action name="MoveToEdge">
        <direction>south</direction>
      </action>
    </keybind>
    <keybind key="W-a">
      <action name="MoveToEdge">
        <direction>west</direction>
      </action>
    </keybind>
    <keybind key="W-d">
      <action name="MoveToEdge">
        <direction>east</direction>
      </action>
    </keybind>

这样就可以使用Windows+c将窗口移动到屏幕中央，
Windows+w将窗口移动到屏幕上侧，
Windows+s将窗口移动到屏幕下侧，
Windows+a将窗口移动到屏幕左侧，
Windows+d将窗口移动到屏幕右侧。

# 窗口的拉伸<a id="orgheadline3"></a>

除了将窗口移动到屏幕的各个方位外，还可以将窗口拉伸到某一边缘：

    <keybind key="W-Up">
      <action name="GrowToEdge">
        <direction>north</direction>
      </action>
    </keybind>
    <keybind key="W-Down">
      <action name="GrowToEdge">
        <direction>south</direction>
      </action>
    </keybind>
    <keybind key="W-Left">
      <action name="GrowToEdge">
        <direction>west</direction>
      </action>
    </keybind>
    <keybind key="W-Right">
      <action name="GrowToEdge">
        <direction>east</direction>
      </action>
    </keybind>

这样就可以使用Windows+Left/Right/Up/Down将窗口拉伸到一定方向的边
缘了。

当然，上面的这些特定的移动在都不能满足需要的时候就需要自己手动调整窗
口的位置了：

    <keybind key="W-m">
      <action name="Move"/>
    </keybind>

这样就可以先按Windows+m然后使用方向键或者鼠标来移动窗口的位置了。

# 窗口的其他操作<a id="orgheadline4"></a>

当然对窗口的一般化的操作都是支持的如最大化，最小化，全屏什么的：

    <keybind key="W-F4">
      <action name="Close"/>
    </keybind>
    <keybind key="W-F8">
      <action name="Resize"/>
    </keybind>
    <keybind key="W-F9">
      <action name="Iconify"/>
    </keybind>
    <keybind key="W-F10">
      <action name="ToggleMaximizeFull"/>
    </keybind>
    <keybind key="W-F11">
      <action name="ToggleDecorations"/>
      <action name="ToggleMaximizeFull"/>
    </keybind>

不过一般我很少使用最大化，常常使用的是水平方向或者垂直方向的单向最大
化窗口：

    <keybind key="W-h">
      <action name="ToggleMaximize">
        <direction>horizontal</direction>
      </action>
    </keybind>
    <keybind key="W-v">
      <action name="ToggleMaximize">
        <direction>vertical</direction>
      </action>
    </keybind>

这样就可以使用Windows+h和Windows+v来将窗口水平最大化和垂直最大化。

# 程序启动快捷键<a id="orgheadline5"></a>

下面是一些常用的的程序启动快捷键，包括启动XTerm, 锁屏，截屏等操作：

    <keybind key="W-q">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>XTerm</name>
        </startupnotify>
        <command>xterm</command>
      </action>
    </keybind>
    <keybind key="W-t">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>XTerm</name>
        </startupnotify>
        <command>xterm -e screen</command>
      </action>
    </keybind>
    <keybind key="W-l">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>XScreensaver</name>
        </startupnotify>
        <command>xscreensaver-command -lock</command>
      </action>
    </keybind>
    <keybind key="Print">
      <action name="Execute">
        <command>scrot -e 'mv $f ~/screenshot/'</command>
      </action>
    </keybind>
    <keybind key="W-Print">
      <action name="Execute">
        <command>scrot -b -s -e 'mv $f ~/screenshot/'</command>
      </action>
    </keybind>
