C-file-operations
=================

File operations using the C language

#include <stdlib.h>
#include <stdio.h>

int main()
{
    //fopen()打开文件返回文件指针
    FILE *fp = fopen("/home/ramosi/today/text.txt","r+");
    //判断文件打开时候成功
    if(fp == NULL)
        return 0;
    
    //fileno()返回指针分配所指文件的文件描述符
    int fd = fileno(fp);
    
    //fdopen()用文件描述符打开文件
    fp = fdopen(fd,"r+");
    //判断文件是否成功打开
    if(fp == NULL)
        return 0;
    
      
    return 0;
}
