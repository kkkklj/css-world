要解释margin无效的原因
当想要通过margin改变自身位置，就必须是和当前定位一样的margin才行，否则的话，margin就只能影响父元素或后面的元素
- margin:auto是为了填充剩余空间设计的
（1）如果一侧定值，一侧 auto，则 auto 为剩余空间大小。
（2）如果两侧均是 auto，则平分剩余空间。
子盒子（比父盒子小）靠右只需要给个margin-right值，然后margin-left:auto，这样盒子的margin-left就会占满左边的剩余空间了。
如果直接margin-left：auto而不指定margin-right(由于margin默认值为0)，marign-left会占满剩余所有空间。