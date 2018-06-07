====================<br/>
<b>这是test01的writeup</b><br/>
1.首先访问index.php 在查看源代码中可以看见‘find a way to GET flag ’这句注释<br/>
2.由此联想到 可能是$_GET['flag']<br/>
3.测试：http://ip/test01/index.php?flag=1  发现出现 '=================' 证明id为flag<br />
4.测试是否为readfile  http://ip/test01/index.php?flag=index.php 发现能够读取到index的源代码<br />
5.在源代码中发现有一句 OTUxNTc0ZmxhZy5waHA= base64解密后发现 为 951574flag.php <br />
6.测试：http://ip/test01/index.php?flag=951574flag.php  提示 请勿使用本方法获取flag值 <br />
7.直接访问 http://ip/test01/951574flag.php  提示 ‘YOU CAN FIND HINT IN THIS PAGE’<br />
8.抓包发现在header中有HINT（FLLLAG）， 打开网址 http://ip/test01/FLLLAG.php  提示‘you get it’ 但是并没有显示flag 。<br />
9.于是用文件读取漏洞进行读取 http://ip/test01/index.php?flag=FLLLAG.php 获取到flag{}<br />
