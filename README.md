# blog_repo
个人博客的源数据仓库，可直接发布生成`blog`页面

## 主题
博客系统使用主题[`hexo-theme-butterfly`](https://github.com/jerryc127/hexo-theme-butterfly)

## 主题生成方法
可以使用npm的方式，和git拉取的方式

## 区别
- npm
  
  使用npm的方式，生成的主题文件在node_modules中
  
  在hexo根目录中执行指令：
  
  ```bash
  npm install hexo-theme-butterfly
  ```
  
  升级方法：在`Hexo`根目录下，运行 `npm update hexo-theme-butterfly`
  
- git
  
  使用git，可以将主题文件生成在themes文件夹中

  获取：

  ```bash
  git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
  ```

  升级方法：在`主题`目录下，运行 `git pull`
