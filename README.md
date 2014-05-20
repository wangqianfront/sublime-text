Sublime Text 使用指南
=================


![sublime_text](https://cloud.githubusercontent.com/assets/692238/3023854/dd9ec488-dfee-11e3-82c2-5220ee871ded.png)

#### 快捷键Shortcuts


* Triggered with <strong>*Ctrl+P*</strong>, it is possible to: 
  - <strong>*Command + P*</strong> 或 <strong>*Command + T*</strong>：搜索打开的文件。再输入 <strong>@</strong> 或 <strong>*Command + R*</strong> 可搜索函数和类；输入 <strong>#</strong> 可在当前文件中搜索；输入<strong> :</strong> 或 <strong>*Control + G*</strong> 可跳转到指定行号。可像使用 CSS 选择器一样组合使用这些符号。Type <strong>@</strong> to jump to symbols, <strong>#</strong> to search within the file, and <strong>:</strong> to go to a line number. 
  - <strong>*Control + `*</strong>：调出 Python 控制台
  - <strong>*Command + ,*</strong>：编辑 Preferences.sublime-settings 文件
  - <strong>*Command + L*</strong>：选择行。重复按下可以增加选择下一行
  - <strong>*Command + D*</strong>：选择词。重复按下可以增加选择下一相同的词
  - <strong>*Command + Return*</strong>：在当前行后插入新行
  - <strong>*Command + Shift + Return*</strong>：在当前行前插入新行
  - <strong>*Command + K*</strong>，<strong>*Command + U*</strong>：切换为大写
  - <strong>*Command + K*</strong>，<strong>*Command + L*</strong>：切换为小写
  - <strong>*Command + X*</strong>：删除行
  - <strong>*Command + /*</strong>：行注释
  - <strong>*Command + Option + /*</strong>：块注释
  - <strong>*Control + Space*</strong>：自动完成。因为和输入法热键相冲突，建议编辑 Preferences - Key Bindings - Default，将“ctrl+space”替换掉，我是使用“alt+tab”
  - <strong>*Control + M*</strong>：跳转到对应的括号
  - <strong>*Control + Shift + M*</strong>：选中当前括号内的内容，重复按下可增加选择括号本身
  - <strong>*Command + Shift + J*</strong>：选中当前缩进级别下的所有代码
  - <strong>*Command + Option + .*</strong>：闭合 HTML/XML 标签
  - 创建符号链接 sudo ln -s "/Applications/Sublime Text 2.app/Contents/SharedSupport/bin/subl" /usr/local/bin/subl
  - <strong>*Command + Shift + P*</strong>：打开命令面板  Show the Command Palette with <strong>*Command + Shift + P*</strong>

  
#### 推荐插件：

1. [emmet](http://docs.emmet.io/)

Package Control：方便安装其他插件。
在控制台中输入如下代码并回车，然后重启 Sublime Text：
    
```
    import urllib2,os;pf='Package Control.sublime-package';ipp=sublime.installed_packages_path();os.makedirs(ipp) if not os.path.exists(ipp) else None;open(os.path.join(ipp,pf),'wb').write(urllib2.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read())
```

SublimeCodeIntel：代码补完提示。输入 . 号即可提示，或者用 Shift + Control + Space 来提示。按住 Option 键再点击变量名，可以跳转到定义变量的地方。

ZenCoding：使用 Control + Option ＋ Return 来调出。
Prefixr：编写 CSS 文件时，可以自动添加 -webkit 等私有词缀。使用 Command + Control + X 来调用。
Tag：自动格式化 HTML，还有其他一些关于标签的功能。使用 Option + Control + F 来调用。
JsFormat：自动格式化 JavaScript。使用 Option + Control + F 来调用。
Case Conversion：切换大小写格式。先按 Option + Control + C，再按 Option + Control + S 切换到下划线分割方式，Option + Control + C 切换到驼峰方式，Option + Control + P 切换到首字母大写方式。
Bracket Highlighter：高亮显示匹配的括号。
Clipboard History：剪贴板历史记录。使用 Control + Option ＋ Command + V 来调出。
WordCount：实时显示字符数。
ConvertToUTF8：编辑非 UTF-8 编码的文本文件。
TrailingSpaces（可以高亮空格并瞬间删除）
Pretty JSON
itGutter
Markdown Preview

#### Snippets：快速输入代码段，这是我最喜欢的功能，不过需要花费时间来设置。
以 JavaScript为例。选择 Preferences - Browse Packages 菜单，打开 JavaScript 文件夹下的 for-()-{}-(faster).sublime-snippet 这个文件：

<snippet>
    <content><![CDATA[for (var ${20:i} = ${1:Things}.length - 1; ${20:i} >= 0; ${20:i}--) {
    ${100:${1:Things}[${20:i}]}$0
};]]></content>
    <tabTrigger>for</tabTrigger>
    <scope>source.js</scope>
    <description>for (…) {…} (Improved Native For-Loop)</description>
</snippet>

其中，content 部分是代码段。${1:Things} 表示光标的初始位置是 Things，并且 2 处 Things 都是被选中的，可以同时编辑。再按下 Tab 键就会跳转到 ${20:i}，它也是可以直接编辑的。再按几次 Tab 键后，最终会来到 $0，它总被当成最后一个序号，当然也可以使用 ${0:// something} 的形式。
tabTrigger 部分是指，输入 fun 再按 Tab 键，就会触发这个 snippet 来进行补完。
scope 是可选的，source.js 表示只对 JavaScript 代码有效。
description 也是可选的，用于简述其用途，代码补完提示时会显示。
自动完成：和 snippets 类似的功能。
以 HTML 为例。选择 Preferences - Browse Packages 菜单，打开 HTML 文件夹下的 HTML.sublime-completions 这个文件：

```
{
    "scope": "text.html - source - meta.tag, punctuation.definition.tag.begin",

    "completions":
    [
        { "trigger": "a", "contents": "<a href=\"$1\">$2</a>" }
        // ...
    ]
}

```

这里的 trigger 表示输入单独的 a 后，按自动完成热键（默认是 Control + Space），就会输出 contents 部分（如果还定义了相同热键的 snippets，则会出现选择菜单），并且光标定位在 $1，编辑完后按 Tab 键，就会跳转到 $2。
在设置中可以设定 "tab_completion": true，这样使用 Tab 键也可以自动完成。如果想插入 Tab 符号，可以用 Shift + Tab。
在现有窗口中打开文件：
按下 Command + , 编辑配置文件，加上这行代码：

```
"open_files_in_new_window": false
```

这样双击打开新文件时，就不会另开一个窗口了。


