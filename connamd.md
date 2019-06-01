# 常用命令

## 文件系统

- 通配符 `?` 代表一个字符 ,`*` 代表0个或多个字符,`[]` 表示一个字符位置给出多个选择，可以是范围。`[axd], [a-x], [1-9]`。`！`排除不需要的内容，`[!a]`。
- 复制文件`cp`。
- 链接文件`ln`。`ln -s source des`。
- 重命名和移动文件`mv`
- 删除文件 `rm -i`。带有提示的删除文件。删除文件需谨慎。
- 删除目录。
  - 空目录`rmdir newdir`。
  - 目录中所有文件。`rm -ri newdir`。
  - 一口气删除目录中所有的东西，`rm -rf newdir`。危险命令，没有提示，没有警告。
- 查看文件内容
  - 查看文件的类型`file`
  - 查看整个文件 `cat`
  - 查看一部分内容 `more`
  - 更方便的more `less`
  - 查看部分文件 `tail` 显示文件末尾10行。`head` 默认显示文件的开头10行
- `tree` 以美观的形式展示目录的内容

## 进程磁盘排序归档

- ps命令，默认只显示当前控制台下的进程 `ps -ef` 。显示系统上的所有进程。`ps -l`产生一个长格式的输出。`ps --forest`显示进程之间的嵌套结构
- top命令实时监测进程
- 结束进程 `kill` ，通过`kill pid`方式。`kill -s HUP 1111`,支持指定的信号类型
  | 信号  | 名称  | 描述  |
  |------|-------|------|
  | 1 |  HUP |挂起   |
  | 2 |  INT |中断   |
  | 3 |  QUIT|结束运行   |
  | 9 |  KILL|无条件终止  |
  |11 |  SEGV|段错误   |
  |15 |  TERM|尽可能终止   |
  |17 |  STOP|无条件停止运行，但不终止   |
  |18 |  TSTP|停止或暂停，后台运行 |
  |19 |  CONT| 在STOP或TSTP之后恢复 |
- `killall` 命令支持通过进程名结束进程。
- 检测磁盘
  - 挂载 `mount`， 手动将u盘`/dev/sdb1`挂载到`/media/disk`可以用到下面的命令`mount -t vfat /dev/sdb1 /media/disk`
  - 卸载设备 `umount [direntory | device]`，如果设备忙用`lsof [path]`显示进程的占用信息，然后停止使用设备或该进程
  - `df`命令显示磁盘的使用情况
  - `du`显示某个目录磁盘使用情况 参数`-c`显示列出文件总的大小`-h`以可读的方式显示大小
- `sort`命令对数据进行排序。`du -sh * | sort -nr`磁盘占用情况反序输出
- 搜索数据`grep [options] pattern [file]`
- 压缩解压缩 `gzip` `gunzip` `zcat`
- 归档数据 `tar -cvf test.tar test/ test2/`。`tar -tf test.tar` 列出tar里面的文件。`tar -xvf test.tar`提取内容。`tar -zxvf filename.tar.gz` 提取`.tar.gz`的文件。

## shell
  
- 进程列表`(pwd;(echo $BASH_SUBSHELL))`，创建子进程执行shell命令。
- 后台模式 `sleep 10 &`, `jobs` 查看后台的作业
- 协程 `coproc sleep 10`， `coproc myjob { sleep 10; }` 设置名字的协程。
- 命名别名 `alias li='ls -li'`。
