http://www.vim.org/scripts/script.php?script_id=1708

Have you ever met that after opening a text file with some kind of encoding you got a bunch of unreadable mess? 
If so, you need FencView.vim. 

Normally, vim detects file encoding based on 'fileencodings' option. For example, if we set this option like this: 
set fileencodings=ucs-bom,GB2312,big5 
Firstly vim try to read file bom. If there is no bom, vim will try to decode the file with GB2312. Unfortunately, the GB2312 and big5 have a lot of overlapped code-points which could lead to a big5-encoded file be decoded with GB2312 by mistake. Then you got mess. 

The 'FencView' uses another approach, let me show you how. 
As we know, take Chinese for example, the occurrence frequency of every character in a normal article is different. For example, '的' is a high frequency character which is encoded to 0xb5c4 in GB2312. However, in Big5 0xb5c4 is the code point for '腔' which is much less frequently used. So we can "guess" the encoding of a file by count up the frequently used characters. It is not 100% accurate but works in most cases. 

The user manual is embeded in fencview.vim, refer to it if you'd like to custmize this script.

If you encounter a file that fencview can not handle, you're more than welcome to send it to me in order to improve the algrithm, but take care of the sensitive data before you do that.
