要解释margin无效的原因
当想要通过margin改变自身位置，就必须是和当前定位一样的margin才行，否则的话，margin就只能影响父元素或后面的元素
- margin:auto是为了填充剩余空间设计的
（1）如果一侧定值，一侧 auto，则 auto 为剩余空间大小。
（2）如果两侧均是 auto，则平分剩余空间。
子盒子（比父盒子小）靠右只需要给个margin-right值，然后margin-left:auto，这样盒子的margin-left就会占满左边的剩余空间了。
如果直接margin-left：auto而不指定margin-right(由于margin默认值为0)，marign-left会占满剩余所有空间。
- margin无效是否可以这样看待margin有效，就是margin对目标元素有效的前提条件是该元素的“流方向”与margin的方向相同才能影响该目标元素。比如普通文档流元素是顺着自左向右、自上而下的，所以margin-left和margin-top可以直接影响目标元素，而margin-bottom和margin-right无法影响目标元素而只能影响兄弟元素。在position为absolute中，是否也可以这样认为，设置的left或right才表示该目标元素产生了向左或向右的流动性，因而可以对left或right设置margin。
