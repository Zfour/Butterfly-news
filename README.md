## 序言：效果展示 ##

![example](https://zfe.space/images/news.png)

![example](https://zfe.space/images/news2.png)

<p>这个插件基于<a style="cursor:pointer"  href="https://www.mxnzp.com/">RollToolsApi</a></p>
<p>在使用前请先在微信搜索小程序“Roll地盘”获取api.id和api.key。</p>

<br>

<b>想体验接口？ </b><br>
可获取临时app_id测试，获取方式：扫描下方小程序码->选择TAB-我的->点击获取临时app_id即可获取临时体验接口的app_id和app_secret，此app_id仅为测试使用，次日凌晨自动重置，重置之后之前生成的app_id将失效，真正使用接口请申请属于自己专属的app_id。

<b>如何注册app_id和app_secret呢？ </b><br>
搜索微信小程序【Roll地盘】，进入我的页面，绑定手机号之后即可获取你的专属app_id和app_secret，使用新方式吧骚年！

<b>捐助api？</b><br>
由于服务器端的维护以及部分接口的维护都是需要付费的，所以如果此项目对您有帮助，还希望您捐赠支持，让我能好好的一直坚持下去。金额不在于多少，一份心意就好！在此感谢捐赠列表中所有的捐赠者，你们的鼓励是我最大的动力！

![example](https://zfe.space/images/juanzhu.png)

<br>

<p>本侧边栏部件通过vuejs进行编码。</p>
<p>资源包地址：https://github.com/Zfour/Butterfly-news</p>
<a  class="btn-beautify button--animated outline black" style="cursor:pointer"  href="https://github.com/Zfour/Butterfly-news">资源包下载</a>
<p>废话不多说了，开始教学。</p>
<hr></hr>

## 步骤1：修改pug代码 ##



### 下载资源包 ###

<a  class="btn-beautify button--animated outline black" style="cursor:pointer"  href="https://github.com/Zfour/Butterfly-news">资源包下载</a>

### 增加、替换代码 ###

<p>将资源包中pug文件夹的card_news.pug文件放入"\themes\butterfly\layout\includes\widget"目录下。</p>
<p>将资源包pug文件夹的index.pug文件放入"\themes\butterfly\layout\includes\widget"目录下替换。(适用于3.1版本以上)</p>
<p>若你的版本较低或存在侧边栏魔改，请打开"\themes\butterfly\layout\includes\widget"路径下的"index.pug"</p>
<p>将card_news代码部分添加至card_author代码块后。添加的代码如下：</p>

```PUG
  if theme.aside.card_news.enable
    !=partial('includes/widget/card_news', {}, {cache:theme.fragment_cache})
```
<p>打开"\themes\butterfly\"路径下的"_config.yml"</p>
<p>搜索到"aside:"设置处</p>
<p>添加news开关代码：</p>

```yml
aside:
  enable: true
  mobile: true    # display on mobile
  position: right # left or right
  card_news:      
    enable: true   
  card_author:
    enable: true
```
<hr></hr>

## 步骤2：添加引入js、css代码 ##

### 放置资源包 ###

<p>将下载包中的news文件夹放入根目录的"source"文件夹下。</p>

### 引入js和css ###

<p>打开"\themes\butterfly\"路径下的"_config.yml"</p>
<p>搜索到"inject:"设置处</p>
<p>添加以下代码：</p>
<p>若已有vue引入，请确保vue的版本为2.6以上。</p>
<p>keys.js一定要放在news.js之前。</p>

```yml
inject:
  head:
  - <link rel="stylesheet" href="/news/css/news.css"/>

  bottom:
  - <script src="https://cdn.jsdelivr.net/npm/vue@2.6.11"></script>
  - <script src="/news/js/keys.js"></script>
  - <script src="/news/js/news.js"></script>
  
```

<hr></hr>

## 步骤3：填写key ##

<p>请获取微信小程序【Roll地盘】中的api.id和api.key。</p>

### 配置key信息 ###

<p>打开'source/news/js/keys.js'文件，将对应的api.id和api.key填入。</p>

```js
const newskey ={
	id:'********',
	key:'*******',	
}
```

<p>此时，"hexo g && hexo s"可发现已加载。</p>

### js文件的加密 ###

<p>在确保加载成功后，需进行js文件的加密。</p>
<p>为了保障自己的key不被泄露及恶意引用，需要对keys.js进行加密处理。</p>
<p>前往<a style="cursor:pointer"  href="https://www.jsjiami.com/">https://www.jsjiami.com/</a>进行js加密。</p>
<p>在点击js混淆加密之前，设置高级选项，进行域名限制防止恶意调用。</p>
<p><b>但这样在localhost时也会禁止调用且会导致浏览器卡死，请在本地调试时将inject的keys.js注释掉。</b></p>
<p>你也可以选择其他加密手段，请确保对引入js的访问限制及加密混淆。</p>

![example](https://zfe.space/images/lock.png)

<hr></hr>
