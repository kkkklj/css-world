# css世界学习总结
### line-height
> 无论内联元素 line-height 如何设置，最终父级元素的高度都是由数值大的
那个 line-height 决定的，我称之为“内联元素 line-height 的大值特性”。

> 只要有“内联盒子”在，就
一定会有“行框盒子”
```html
<div class="box">
  <span>内容...</span>
</div>
```
### height
- 外联元素默认占满一行，所以即便是width:auto，效果也相当于100%。(规范未定义，是各浏览器默认相当于100%，算明确值了)
- 但盒子的高度并不是一个确定的数值，height:auto并不是一个明确的值
- 另外绝对定位的百分比高是按照padding box计算的(有算padding),而非绝对定位是相对于content box计算的。
```
发现了一个有意思的特性，auto到某一具体值的变化transition动画是不会有过渡效果的(待验证)，只有具体值到具体值才会有过渡效果，因为张鑫旭在P39是这样证实min-height默认值为auto的（transition没有效果）
max-height的收拉
```
# 内联元素
> 在 CSS 世界中，内联元素是最为重要的，涉及的 CSS 属性也非常之多，这些 CSS 属性
往往具有继承特性，混合在一起会导致 CSS 解析规则非常复杂。这就是内联元素的解析比块级
元素解析更难理解的原因
>> “内联元素”的“内联”特指“外在盒子”
>>> inline-block 和 inline-table 都是“内联元素”，因为它们的“外在盒子”都是内联盒子。

# 盒尺寸4大家族
## content
> 通过修改某个属性值呈现的内容就可以被替换的元素就称为“替换元素”。我个人将替换元素的尺寸从内而外分为 3 类：固有尺寸、 HTML 尺寸和 CSS 尺寸。
>> 固有尺寸指的是替换内容原本的尺寸

>> HTML 尺寸不妨将其想象成水煮蛋里面的那一层白色的膜

- 尺寸的优先级: 固有<HTML<CSS

*这样也是为什么图片光设置了宽度之后,图片依旧有高度的原因,这是因为图片的固有尺寸*
- 图片懒加载

然后配合下面的 CSS 可以实现一样的效果：
```css
img { visibility: hidden; }
img[src] { visibility: visible; }
```
注意，这里的img标签直接没有 src 属性，再强调一遍，是直接没有，不是 src=""， src=""
在很多浏览器下依然会有请求，而且请求的是当前页面数据。当图片的 src 属性缺省的时候，
图片不会有任何请求，是最高效的实现方式。
> 好了，最后和标题再呼应下，替换元素和非替换元素的距离有多远？就是 src 或 content那一点。
## padding
>> 很多人可能有这样的误区，认为设置了 box-sizing:border-box， 元素尺寸就不会变化。大多数情况下是这样的，但是，如果 padding 值足够大，那么 width 也无能为力了。
- 内联元素没有可使宽度和高度（clientHeight和clientWidth永远是0），垂直方向的行为完全受line-height和vertical-align影响。
- 对于内联元素来说，padding是会存在的，但它的padding不会影响文档流，甚至可以理解为它的padding就不存在文档流中，虽然我们可以用background-color让它显示出来。但是非常神奇的是，该内联元素的父元素设置overflow:auto的时候，却能出现滚动条。
>> 由此可见，内联元素 padding 对视觉层和布局层具有双重影响，所有类似“垂直方向padding 对内联元素没有作用”的说法显然是不正确的。
- 内联元素padding妙用，在不影响文档流的情况下改变内联元素的位置（锚点定位遇到fixed导航）
- padding百分比是按照宽度计算的
*** 科普一下，offsetHeight/offsetWidth（包含padding和border），clientHeight/clientWidth（包含padding但不包含border） ***
- margin只有元素的尺寸表现符合“充分利用可利用空间”的时候才可以改变尺寸大小。
- margin合并规则总结为“正正取大值”“正负值相加”“负负最负值”

