htop 备忘清单
===

htop 是一个交互式流程查看器，此 htop 备忘清单包含 htop 命令

入门
----

### htop 用法

htop 是一个互动的进程查看器，动态观察系统进程状况

- [命令 htop 的官网](https://htop.sourceforge.net/)

```bash
$ htop [-dChustv]
```

#### 安装

```bash
$ apt install htop        # Debian
$ dnf install htop        # Fedora
$ emerge sys-process/htop # Gentoo
$ pacman -S htop          # Arch Linux
$ Compile htop            # GoboLinux
```

htop 的软件包在大多数发行版中都[可用下载](https://htop.dev/downloads.html)

### 选项示例
<!--rehype:wrap-class=col-span-2-->

长选项的强制参数对于短选项也是强制的

:- | :-
:- | :-
`-d --delay=DELAY` | 更新之间的延迟，以十分之一秒为单位
`-C --no-color --no-colour` | 以单色模式启动 `htop`
`-h --help` | 显示帮助消息并退出
`-p --pid=PID,PID...` | 仅显示给定的PID
`-s --sort-key COLUMN` | 按此列排序(对列列表使用`--sort-key`帮助)
`-u --user=USERNAME` | 仅显示给定用户的进程
`-v --version` | 输出版本信息并退出
`-t --tree` | 在树状视图中显示流程

### 状态

:- | :-
:- | :-
`R`  | 运行中
`S`  | 休眠
`T`  | 追踪/停止
`Z`  | 僵尸
`D`  | 磁盘睡眠
<!--rehype:className=shortcuts-->

### 交互式命令
<!--rehype:wrap-class=col-span-2 row-span-3-->

:- | :-
:- | :-
`F1`, `h`, `?` | 转到帮助屏幕
`F10`, `q` | 退出
`Space` | 标记或取消标记进程
`U` | 取消标记所有进程(删除所有使用 Space 键添加的标记)
`s` | 跟踪进程系统调用：如果安装了 `strace(1)`，按下此键会将其附加到当前选定的进程，呈现进程发出的系统调用的实时更新
`l` | 显示进程打开的文件：如果安装了 `lsof(1)`，按下该键将显示进程打开的文件描述符列表
`F2`, `S` | 转到设置屏幕，您可以在其中配置屏幕顶部显示的仪表，设置各种显示选项，在配色方案中进行选择，并选择显示的列，以何种顺序显示
`F3`, `/` | 逐步搜索所有显示进程的命令行。当前选定(突出显示)的命令将在您键入时更新。在搜索模式下，按 `F3` 将循环匹配出现的事件
`F4`, `\` | 增量进程过滤：输入部分进程命令行，仅显示名称匹配的进程。要取消过滤，请再次输入过滤选项并按 `Esc`
`F5`, `t` | 树视图：按父级组织进程，并将它们之间的关系布局为树。切换键将在树和您之前选择的排序视图之间切换。选择排序视图将退出树视图
`F6` | 在排序视图上，选择一个字段进行排序，也可以通过 < 和 > 访问。当前排序字段由标题中的突出显示。在树视图中，展开或折叠当前子树。树节点中的“+”指示符表示它已折叠
`F7`, `]` | 增加所选进程的优先级(从“nice”值中减去)。这只能由超级用户完成
`F8`, `[` | 降低选定进程的优先级(添加到“nice”值)
`F9`, `k` | “杀死”进程：向一个或一组进程发送一个在菜单中选择的信号。如果进程被标记，则将信号发送到所有标记的进程。如果没有标记，则发送到当前选定的进程
`+`, `-` | 在树视图模式下，展开或折叠子树。
`a` | (在多 CPU 机器上)设置 CPU 亲和性：标记允许进程使用的 CPU
`u` | 仅显示指定用户拥有的进程
`F` | “跟随”进程：如果排序顺序导致当前选定的进程在列表中移动，则使选择栏跟随它。这对于监控进程很有用：这样，您可以使进程始终在屏幕上可见。使用移动键时，“跟随”失效。
`p` | 在适用的情况下显示运行程序的完整路径(这是一个切换键)
`Ctrl-L` | 刷新：重绘屏幕并重新计算数值
`Numbers` | PID搜索：输入进程ID，选择突出显示将移至它
<!--rehype:className=shortcuts-->

### 排序/线程

:- | :-
:- | :-
`M` | 按`内存`使用情况排序 _(最高兼容性键)_
`P` | 按`CPU`使用情况排序 _(最高兼容性键)_
`T` | 按`时间`排序 _(最高兼容性键)_
`I` | `反转`排序顺序
`K` | 隐藏`内核`线程
`H` | 隐藏`用户`线程
<!--rehype:className=shortcuts-->

### 滚动

:- | :-
:- | :-
`Up`, `Alt-k` | 在流程列表中选择(突出)`上`一个流程
`Down`, `Alt-j` | 在流程列表中选择(突出)`下`一个流程
`Left`, `Alt-h` | 向`左`滚动流程列表
`Right`, `Alt-l` | 向`右`滚动进程列表
`PgUp`, `PgDn` | 将流程列表`向上`或`向下`滚动一个窗口
`Home` | 滚动到流程列表的`顶部` <br /> _选择第一个流程_
`End` | 滚动到流程列表的`底部` <br /> _选择最后一个流程_
`Ctrl-A`, `^` | 向`左`滚动到流程条目`开头` _(即行开头)_
`Ctrl-E`, `$` | 向`右`滚动到流程条目`末尾` _(即行尾)_
<!--rehype:className=shortcuts-->