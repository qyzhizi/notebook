Linux shell ${}简单用法<Br/>
[转]http://linux.chinaunix.net/techdoc/develop/2007/05/05/956956.shtml<Br/>

为了完整起见，我这里再用一些例子加以说明 ${ } 的一些特异功能：<Br/>
假设我们定义了一个变量为：<Br/>
```
file=/dir1/dir2/dir3/my.file.txt
```
我们可以用 ${ } 分别替换获得不同的值：
```
${file#*/}：拿掉第一条 / 及其左边的字符串：dir1/dir2/dir3/my.file.txt
${file##*/}：拿掉最后一条 / 及其左边的字符串：my.file.txt
${file#*.}：拿掉第一个 . 及其左边的字符串：file.txt
${file##*.}：拿掉最后一个 . 及其左边的字符串：txt
${file%/*}：拿掉最后条 / 及其右边的字符串：/dir1/dir2/dir3
${file%%/*}：拿掉第一条 / 及其右边的字符串：(空值)
${file%.*}：拿掉最后一个 . 及其右边的字符串：/dir1/dir2/dir3/my.file
${file%%.*}：拿掉第一个 . 及其右边的字符串：/dir1/dir2/dir3/my
```
记忆的方法为：<Br/>

`# 是去掉左边(在鉴盘上 # 在 $ 之左边)`

`% 是去掉右边(在鉴盘上 % 在 $ 之右边)`

`单一符号是最小匹配﹔两个符号是最大匹配。`

```
${file:0:5}：提取最左边的 5 个字节：/dir1
${file:5:5}：提取第 5 个字节右边的连续 5 个字节：/dir2
我们也可以对变量值里的字符串作替换：
${file/dir/path}：将第一个 dir 提换为 path：/path1/dir2/dir3/my.file.txt
${file//dir/path}：将全部 dir 提换为 path：/path1/path2/path3/my
```
