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
    
    //fseek()将文件指针偏转offset
    //fseek(fp,0,SEEK_END);
    
    char a[16] = "The first line!";
    for(int i = 0; i < 15; i++)
    {
        //fputc()每次写入文件一个字符
        fputc(a[i],fp);
    }
    
    //rewind()将文件指针重新置到起始处
    rewind(fp);
    
    char c;
    //fgets()每次从文件读一个字符，返回所读字符
    while((c = fgetc(fp)) != EOF)
        printf("%c", c);
    printf("\n");
    
    char put[] = "fputs function!";
    char *puts = put;
    //fputs()每次写入文件一个字符串
    fputs(puts,fp);
    
    char s[100];
    rewind(fp);
    //fgets()每次读直到换行或EOF
    fgets(s,99,fp);
    
    printf("%s\n",s);
    
    //fclose()关闭文件
    fclose(fp);
    
    return 0;
}
