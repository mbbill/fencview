http://www.vim.org/scripts/script.php?script_id=1708

Have you ever met that after opening a text file with some kind of encoding you got a bunch of unreadable mess? 
If so, you need FencView.vim. 

Normally, vim detects file encoding based on 'fileencodings' option. For example, if we set this option like this: 
set fileencodings=ucs-bom,cp936,big5 
Firstly vim try to read file bom. If there is no bom, vim will try to decode the file with cp936. Unfortunately, the cp936 and big5 have a lot of overlapped code-points which could lead to a big5-encoded file be decoded with cp936 by mistake. Then you got mess. 

The 'FencView' uses another approach, let me show you how. 
As we know, take Chinese for example, the occurrence frequency of every character in a normal article is different. For example, '的' is a high frequency character which is encoded to 0xb5c4 in GB2312. However, in Big5 0xb5c4 is the code point for '腔' which is much less frequently used. So we can "guess" the encoding of a file by count up the frequently used characters. It could not handle every file but it works in most cases. 


