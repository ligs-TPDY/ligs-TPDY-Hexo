# ligs-TPDY-Hexo
Hexo文件夹。本地终端使用该文件编辑博客
## 一，Mac下利用Hexo+GitHub轻松搭建自己的博客
### Hexo安装
#### 1，基本流程：
###### 1.hexo是基于nodejs的，需安装nodejs，安装nodejs最好选择homebrew
###### 2.首先查看电脑是否安装ruby，因为homebrew安装依赖ruby
###### 3.安装顺序：homebrew---->nodejs---->hexo
#### 2，具体安装流程：
###### 1,安装homebrew终端命令：	 
                  
    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
###### 2,安装nodejs终端命令：

	brew install node
	
###### 在安装nodejs过程中，提示如下警告：
	You have Xcode 8 installed without the CLT;
###### 根据提示进行安装
		
###### 3，安装hexo终端命令:

	sudo npm install -g hexo
### Hexo安装成功

### 本地工作空间
###### 1，创建本地文件夹，在该文件夹中启动Hexo工作，注意自己注意创建的目录：
	mkdir blog 		新建文件
	cd blog 			打开新建的文件
	hexo init		在当前文件夹中初始化hexo
###### 2，我们先不写东西，只是生成hexo默认的一个界面，看下效果：
	hexo generate 	/** 生成一套静态网页 **/
	hexo server 		/** 在服务器上运行 **/
###### 3，在浏览器中打开下面的地址，就可以看到默认的界面主页
	http://localhost:4000
### 本地工作空间创建完毕

### 关联到GitHub
###### 1，我们先不急着写博客，先解决一个问题，就是本地创建的博客文件，如何同步到GitHub中？这里有一种比较方便的方法，可以自动同步你的文件到GitHub。那就是使用Hexo的配置文件来处理。
	Hexo的每一个功能的配置文件都是_config.yml， 具体说明看下面的注解：
	# Hexo Configuration
	## Docs: https://hexo.io/docs/configuration.html
	## Source: https://github.com/hexojs/hexo/
 
	# Site                 ##修改以适应搜索引擎的收录
	title: Hexo            ##定义网站的标题
	subtitle:              ##定义网站的副标题
	description:           ##定义网站的描述
	author: jason jwl      ##定义网站的负责人
	language:              ##定义网站的语言,默认zh-Hans
	timezone:              ##定义网站的时区
 
	# URL
	## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
	url: http://yoursite.com   ##定义网站访问的域名
	root: /      ##定义所在Web文件夹在哪个目录
	permalink: :year/:month/:day/:title/  ##定义时间格式
	permalink_defaults:
 
	# Directory
	source_dir: source   ##定义从哪个文件夹获取博客资料
	public_dir: public   ##定义生成静态网站到哪个文件夹
 
	archive_dir: archives
	category_dir: categories
	code_dir: downloads/code
	i18n_dir: :lang
	skip_render:
 
	# Writing
	new_post_name: :title.md # File name of new posts
	default_layout: post
	titlecase: false # Transform title into titlecase
	external_link: true # Open external links in new tab
	filename_case: 0
	render_drafts: false
	post_asset_folder: false
	relative_link: false
	future: true
	highlight:
  	enable: true
  	line_number: true
  	auto_detect: false
  	tab_replace:
 
	# Category & Tag
	default_category: uncategorized
	category_map:
	tag_map:
 
	# Date / Time format
	## Hexo uses Moment.js to parse and display date
	## You can customize the date format as defined in
	## http://momentjs.com/docs/#/displaying/format/
	date_format: YYYY-MM-DD
	time_format: HH:mm:ss
 
	# Pagination
	## Set per_page to 0 to disable pagination
	per_page: 10  ##定义每一页多少条博客
	pagination_dir: page
 
	# Extensions
	## Plugins: https://hexo.io/plugins/
	## Themes: https://hexo.io/themes/
	theme: landscape  ##定义使用的主题
 
	# Deployment
	## Docs: https://hexo.io/docs/deployment.html
	deploy:
  	type:
###### 那么，如何实现文件自动同步呢？注意配置文件的最后一部分，我们将在那里配置GitHub。
	deploy:
  		type: git
  		repo: https://github.com/xxx/xxx.github.io.git
  		branch: master
  （xxx为个人github的name）
### 关联到GitHub完成

### 让我们来创建一篇自己的博客吧
###### 首先进入终端，使用cd命令进入到有Hexo框架的目录里面（bolg），输入：
	hexo new post "我的第一篇博客"
	(注意，该文件可以使用Markdown的编辑文件编辑，Hexo会自动转化为静态页面)
###### 然后输入：hexo generate 或者 hexo g 	/** 生成一套静态网页 **/
###### 最后将该页面同步到GitHub上去，输入Hexo deploy 或者 Hexo d,该静态页面就会同步到GitHub上。
### 创建一篇自己的博客完成

### 如何访问GitHub上的静态页面呢
###### 从《本地工作空间》我们知道，可以在自己电脑上启动Hexo服务器，然后通过固定的地址就可以看到我们自己定义的界面。我们后来自己创建的博客也会出现在这个界面，但毕竟是我们本地的服务器，访问上很不方便。如何让远在五湖四海的兄弟都能看到你最新的博客呢？对，答案就是将Hexo生成的静态页面托管到GitHub上。上面的工作，我们已经顺利的将静态页面托管到了GitHub上，接下来就是如何访问他们了？
### 创建自己的GitHub Pages
### 创建自己的GitHub Pages完成

## 二，快速、简洁且高效的博客框架
###### Hexo官网：
https://hexo.io/zh-cn/
	
 





	





	
