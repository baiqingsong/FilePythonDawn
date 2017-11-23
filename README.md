# Python中的文件处理

* [文件的打开和读写](#文件的打开和读写)
* [文件的属性](#文件的属性)
* [os模块对文件和目录的操作](#os模块对文件和目录的操作)

## 文件的打开和读写
文件的打开方法：open(name, [, mode[buf]])  
name:文件的路径  
mode:打开方式  
buf:缓冲buffering的大小  
文件的读取方式：  
read([size]):读取文件（读取size个字节，默认全部读取）  
readline([size]):读取一行  
readlines([size]):读取多行，返回每一行所组成的列表，size不起作用  
iter：使用迭代器读取文件  
文件写入方式：  
write(str):将字符串写入文件  
writelines(sequence_of_strings):写多行到文件，参数为可迭代的对象，必须时字符串组成的序列  
文件打开方式  
`r`       只读方式打开       文件必须存在  
`w`       只写方式打开       文件不存在创建，文件存在清空文件  
`a`       追加方式打开       文件不存在创建  
`r+` `w+` 读写方式打开  
`a+`      追加和读写方式打开  
`rb`,`wb`,`ab`,`rb+`,`wb+`,`ab+`:二进制方式打开  
关闭：  
close()  
文件指针操作：  
seek(offset[, whence]):移动文件指针  
offset:偏移量，可以为负数  
whence:偏移相对位置  
Python文件指针定位方式（whence）：  
os.SEEK_SET:相对文件起始位置  
os.SEEK_CUR:相对文件的当前位置  
os.SEEK_END:相对文件的结尾位置  
偏移量过界会报IOError错误  

## 文件的属性
file.fileno():文件描述符  
file.mode:文件的打开权限  
file.encoding:文件编码格式  
file.closed:文件是否关闭  

Python标准文件  
1. 文件标准输入：sys.stdin  
2. 文件标准输出：sys.stdout  
3. 文件标准错误：sys.stderr  
sys.argv:字符串组成的列表  

使用codecs模块提供方法创建指定编码格式文件  
open(fname, mode, encoding, errors, buffering):使用指定编码格式打开文件  

## os模块对文件和目录的操作
os.open(filename, flag[, mode]):打开文件  
flag：打开文件方式  
os.O_CREAT:创建文件  
os.O_RDONLY:只读方式打开  
os.O_WRONLY:止血方式打开  
os.O_RDWR:读写方式打开  

os.read(fd, buffersize):读取文件  

os.write(fd, string):写入文件

os.lseek(fd, pos, how):文件指针操作

os.close(fd):关闭文件

os的其他常用方法：
access(path, mode):判断该文件权限：F_OK存在，权限：R_OK,W_OK,X_OK  
listdir(path):返回当前目录下所有文件组成的列表  
remove(path):删除文件  
rename(old, new):修改文件或者目录名  
mkdir(path[,mode]):创建目录  
makedirs(path[,mode]):创建多级目录  
removedirs(path):删除多级目录  
redir(path):删除目录（目录必须空目录）  

os.path的相关方法
exists(path):当前路径是否存在  
isdir(s):是否是一个目录  
isfile(path):是否是一个文件  
getsize(filename):返回文件大小  
dirname(p):返回路径的目录  
basename(p):返回路径的文件名  

ini文件的操作  
ini配置文件的格式：  
节：[session]  
参数（键=值）：name=value  

cfg = ConfigParser.ConfigParser()创建对象  
cfg.read(文件名)：解析文件
cfg.sections()返回所有节的列表  
cfg.items(节的名称)返回节当中的所有内容（键值）  
cfg.add_section(节的名称)：添加节
cfg.set(节的名称，节内容的键名，节内容的值)：如果键存在是修改，键不存在是添加  
cfg.remove_option(节内容的键名)：删除内容  
cfg.remove_section(节的名称)：删除节  
