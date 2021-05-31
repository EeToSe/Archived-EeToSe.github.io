---
layout: default
title: Software Tool
nav_order: 6
parent: Linux
---
# Useful Software Tools Introduction
{: .no_toc}
This section records the applications which I have used during the various programs and the related problems :)
{: .no_toc .text-delta }
1. TOC
{:toc}
## Zotero Update
**Problem**: A recommended update is available but you don't have permission to install it. To update automatically, modify the Zotero program directory to be writeable by your user account.

**Cause**: Zotero is installed in a folder where the normal user dont have write permissions(/opt in my case). The standard install location would be somewhere on ~/.local 

**Solution**: COMBINE the numeric permissions listed below.
400 read by owner
040 read by group
004 read by anybody
200 write by owner
020 write by group
002 write by anybody
100 execute by owner
010 execute by group
001 execute by anybody
775 give all permission except write by anybody; 777 makes the directory writable, readable and executable by anybody

## img2pdf
I wish I could have known this amazing software a couple of years. It is just elegant and efficient to solve the file conversion in Linux.
**Task**: Convert images to pdfs.

**Problem**: I still dont understand the mess with [Imagemagick](https://stackoverflow.com/questions/52998331/imagemagick-security-policy-pdf-blocking-conversion)

**Soultion**: [img2pdf](https://askubuntu.com/questions/246647/convert-a-directory-of-jpeg-files-to-a-single-pdf-document)
```sh
# combine all jpgs into one pdf
img2pdf --out test.pdf *.jpg
# combine jpg to pdf format one by one
for file in *.jpg; do img2pdf --out "${file%.jpg}.pdf" "$file"; done
```
Explanation for code: `$` 用于引用变量的值
[What does `%` do in bash?](https://superuser.com/questions/1119290/what-does-do-in-linux-shell-strings):When % is used in pattern ${variable%substring} it will return content of variable with the shortest occurance of substring deleted from back of variable.

## pdftk/ qpdf
**Task**: Extract the first pages of 70 papers and combine them into one pdf sequentially.

[**Origin Solution**](https://superuser.com/questions/207414/extract-first-page-from-multiple-pdfs): 
Step1: Extract first page from multiple pdfs
```sh
for file in *.pdf ; do pdftk "$file" cat 1 output "${file%.pdf}-page1.pdf" ; done
```
Step2: Combine the results into one pdf
```sh
pdftk *-page1.pdf cat output combined.pdf
```
**Advance**: How to do it in order?
Use sort to understand how the files are sorted in linux.举个栗子
```sh
ls | sort -k1.1,1.3
```
man sort or see [this page](https://stackoverflow.com/questions/6297906/linux-sort-only-by-the-first-letter-of-each-line) 
<p align = "center">
<img src="/assets/image/sort-right.png" alt="hi" class="inline"/>
<em>Files are sorted sequentially</em>
</p>

<p align = "center">
<img src="/assets/image/sort-wrong.png" alt="hi" class="inline"/>
<em>Files are not sorted sequentially (pay attention to the sequence <span style="color:red">'1.XXXX'</span>)</em>
</p>



