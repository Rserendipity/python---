import requests
import re
import os
from urllib.parse import quote
import random
def  movie(url_be):  #封装解析并下载电影函数movie
    response =requests.get(url=url_be).text  #get方式获取原页面内容
    # print(response)
    # print(url_gl)
    url =re.search(r"url=(.*m3u8)",response).group(1)  #在以上基础上使用正则提取m3u文件
    print(url)
    name =input('[+]输入保存的文件名(加扩展名):')
    cmd ="movie -i " + url + " -vcodec copy -acodec copy " + name
    print("[-]正在加载中.......画质：高清 保存位置：当前目录下")
    print("[-]视频正在下载中 请勿关闭！！！否则进度将丢失")
    print("[-]原视频的长度取决于你是否又耐心等待，下载的速度等同于你的网速....<字母Q退出下载!!!!!>")
    os.system(cmd)
    print("[-]如果没有返回[https @ 000002a4e80fa280] Opening 'https：//xxxxx' for reading则说明此链接解析失败！！")
def online():
    url=input("[+]输入你想观看的vip视频的地址链接：")
    print("[-]解析成功，复制下面链接到浏览器访问")
    url_online="https://jx.618g.com/?url="
    url_encode = quote(url, 'gbk')
    print(url_online+url_encode)
print("[+]-------欢迎使用vip视频抓取-------[+]")
print("作者：昌晶晶. QQ:2249077862. 电话：13277482396.")
print("-"*50)
boss =input("[1]在线观看 [2]下载到本地 输入 (1 or 2):")
if boss=="1":
    online()
    ps=input("输入任意键结束程序...")
if boss=="2":
    url_gl =input("[+]输入要爬取的URL链接:")
    print("[-]正在解析......请稍等......")
    movie_url="https://jx.618g.com/?url="+url_gl
    #print(movie_url)
    print(movie(movie_url))
    ps = input("输入q结束程序...")
else:
    print("[*]你是憨憨嘛，输错了！")
