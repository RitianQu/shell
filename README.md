#### shell脚本的本质:shell命令的有序集合
#### 建立shell脚本的过程
###  1 建立文件并编译 （文件以 .sh 为后缀。文件名原则上用字母数字下划线的组合，通常以字母开头有一定意义为好）
###  2 修改权限  将编辑的脚本添加可执行权限
###  3 执行  如果脚本有可执行权限 可以用./filename 直接执行
###         如果没有执行权限 可以使用 bash filename 声明解释器执行
#### 变量：需要是合法的标示符
###  1 数字字母下划线组成
###  2 不能以数字开头
###  3 不能和关键字重名（shell 命令）
###  4 shell中是区分大小写的
#### 数字和字符串类型
     shell是弱类型语言
### 注意点：变量赋值时等号两边不要有空格
###        可以用unset删除一个变量的赋值
###        在取变量值的时候用$
#### 位置变量：在执行脚本时，通过命令行进入的参数就叫做位置变量
###  $0 脚本名
###  $1 -9 表示1-9 9个位置的传入
###  ${10}
###  传入字符串中间有空格需要用“”
###  $# 命令行参数的个数，不包含命令本身
###  $? 显示前一个命令的推出状态，如果正常为0，否则为非0
#### export 添加环境变量
###  HOME PATH
     export PATH+=":/home/linux/shell"
#### read:从终端获取变量
###  1 一个read对应一个回车
#### expr 简单的表达式运算
          注意：运算符两边药加空格
          eg： echo `expr 1 + 5`
#### let: 多种运算
###  + - * / % += -+。。。。。
###  << >> ^ & | ~
#### bc:小数运算
#### 测试：
#### True False
#### test 语句
###  数字 字符串 文件
##   整数测试； a -eq b 测试a与b是否相等
##            a -ne b 测试a与b是否不想等
##            a -gt b 测试a是否大于b
##            a -ge b 测试a是否大于等于b
##            a -lt b 测试a是否小于b
##            a -le b 测试a是否小于等于b
##   字符串测试；s1 = s2测试两个字符串的内容是否完全一样
##             s1 != s2测试两个字符串的内容是否有差异
##             -z s1  测试s1字符串的长度是否为0
##             -n s1  测试s1字符串的长度是否不为0
##   文件测试； -d name 测试name是否为一个目录
##             -e name 测试一个文件是否存在
##             -f name 测试name是否为普通文件
##             -L name 测试name是否为符号链接
##             -r name 测试name文件是否存在且为可读
##             -w name 测试name文件是否存在且为可写
##             -x name 测试name文件是否存在且为可执行
##             -s name 测试name文件是否存在且其长度不为0
##             f1 -nt f2 测试文件f1是否比文件f2更新
##             f1 -ot f2 测试文件f1是否比文件f2更旧
###  用[]的形式 不要忘了空格
#### &&=-a ||=-o ！
###  与：一假则假 [ 1 -eq 2 -a 1 -eq 1]  [ 1 -eq 2 ] && [ 1 -eq 1 ]
###  或：一真则真 [ 1 -eq 2 -o 1 -eq 1]  [ 1 -eq 2 ] || [ 1 -eq 1 ]
###  非：真变假 假变真 ！ [ 1 -eq 2 ]
#### if语句
###  1.简单的if语句
     if  表达式
     then 
         命令表
     fi
#### case语句
###   case 字符串变量 in
###     模式1）
###         命令表1
###         ；；
###     模式2 | 模式3）
###         命令表2
###         ；；
###     模式n）
###         命令表n
###         ；；
###     esac
#### for循环
     for  变量名   in  单词表
     do
       命令表
     done 
#### 简单的 for 用法
     {1..100..2}
     没有单词表的情况，直接从命令行传入单词表
     累c语言的写法
#### while 循环：
     while 逻辑表达式
     do
       命令表
     done
#### continue 结束本次循环，继续执行下次循环
#### 什么是死循环
#### break 终止循环
#### 什么是死循环 true false
#### 函数：
       1 函数必须先定义后使用
       2 目的：为了代码的复用，是封装性的基本体现
       3 在shell中函数的定义和实现是在一起的
       4 函数的三要素：功能 参数 返回值
       5 在shell中也有内建函数和自定义函数
       基本格式
       function_name () {
       dommand1
       ......
       commandn
       }
#### 作用域
     局部作用域：只有在作用范围内可以使用
     在函数内：local name
     全局作用域：可以在文件的任意地方使用
               当局部变量与全局变量重名时，在局部回默认使用局部
#### 递归函数：函数内部调用自身
     注意：要有结束条件
#### &&列表：直到有一个为false就不再执行
#### ||列表：如果有一个是True就不再执行下一个
#### set-e 打开错误调试
#### set +e 关闭错误调试
#### set -x 分步显示执行过程
#### 数组 ： 数据饿集合
###  如何定义数组
###  数组取值
     打印
     便利
     求长度
     邱某一个元素的长度
#### 正则表达式













###  支持多种编程语言及脚本
###  在shell中通常与 grep find sed awk 等命令一起使用
#### 规则
     ×   匹配0或多个在×字符之前的哪个普通字符
     .   匹配任意一个字符
     ^   匹配行首
     ￥  匹配行尾
     ^$  匹配空行
     ^....$ 匹配一整行的内容
     []  匹配字符集合 1-9 a-z A-Z
     [^...] 匹配除了...之外的
     \   转义字符
     \<...\>  精确匹配
     \{n\}  匹配前面字符出现n次
     \{n，\}  匹配前面字符至少出现n次
     \{n，m\}  匹配前面字符出现n-m次
     ？   匹配0个或1个之前的字符
     +   匹配1个或多个之前的哪个普通字符
     ()  表示一个字符集合
     |   表示或   （a | b | c）--->[abc]
#### sed 命令及sed编程
#### sed是一个非交互式的文本编辑器
#### sed 主要一个用场景
         1.编辑相对交互式文本编辑器而言太大的文件
         2.编辑命令太复杂，在交互式文本编辑器中那一输入
         3.对文件扫描一遍，但是需要执行多个编辑函数的情况。
#### 运行
     1.在shell命令行输入sed命令
     sed [选项] ‘sed命令’ 输入文件
     2.将sed命令插入脚本执行
     ./sed
     选项
     -n:不打印所有行到标准输出
     -e：表示下一个字符串是sed命令
     -f：表示正在调用脚本文件
     -i：直接修改操作文件内容
     命令
     1.药操作的范围
       使用行号或者正则表达式
       x  指定行号
       x,y指定从x行到y行
       x，y！ 指定不包含x和y行的行
       /pattern/  查询包含模式的行
       /pattern/pattern/ 多个模式
       /pattern/，x 从匹配行到x行
       x,/pattern/ 从x行到匹配行
     2.具体命令
       p 打印匹配行
       = 打印文件行号
       a\在定位行之后追加文本信息
#### 打开终端
     ctrl alt t 打开终端
     ctrl alt n 打开相同目录下的终端
     ctrl alt t 同一终端打开终端  ctrl num 切换
     exit 退出
#### vim 
     i 光标前插入  I行首  o下一行 O当前行 a光标后 A行尾
     s 删除光标所在字符进入插入模式
     S 删除光标所在行进入插入模式
#### 光标的跳转
     b单词开头  e单词结尾  w下一个单词 0行首  $行尾  gg首行  G末行
     cc 删除当前那行进入插入模式
     c + b|e|w|0|$  删除光标到指定位置进入插入模式
     y + b|e|w|0|$  复制光标到指定位置
     u  撤销上一步操作
     ctrl + r  反撤销
     x  删除字符
     r  替换字符
     R  进入替换状态直到esc退出
     /  进入底行查找  n进行查找跳转  noh 去除高量
     ： 进入底行命令 
     ：n,my  第n行复制到m行
     ：n,md  第n行剪切到m行
     ：w filename 保存一个新文件
     ：read filename
     ：%s/oldword/newword/g 替换
     ：vsp 左右分屏
     ：sp  上下分屏
     
