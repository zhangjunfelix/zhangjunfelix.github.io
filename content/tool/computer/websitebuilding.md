---
title: "Create static websites"
date: 2023-08-12T15:02:40+08:00
draft: false
hidden: true

---

Sure, I'll revise the codes for clarity and aesthetics. Here's the improved version:

---

### **Hugo**

**Here are some of the codes/tips that I used in creating my website:**

1. **Commonly used commands**  
    - Change directories:  
      ```bash
      cd
      ```
    - Create a new site (yml or toml):  
      ```bash
      hugo new site anatole-felix -f yml
      cd anatole-felix
      ```
    - Clone Anatole theme:  
      ```bash
      git clone https://github.com/lxndrblz/anatole.git themes/anatole --depth=1
      ```
    - Open folder in VS Code:  
      ```bash
      code .
      ```
    - Start local server:  
      ```bash
      hugo server
      ```
      (Add `-D` to include draft pages)

2. **Commands to modify `config.toml`**  
    2.1 **Add favicon**  
        - Step 1: Generate and download favicon from favicon.io  
        - Step 2: Extract and copy all files to the `static` root directory  
        - Step 3: Add the following line to `themes/anatole/layouts/partials/head.html`:  
          ```html
          <link rel="shortcut icon" href="favicon.ico" />
          ```
          (Replace `favicon.ico` with the appropriate file name if different)  
          Refer to this guide for more details.

    2.2 **Create a new blog or post**  
        - Create a new post:  
          ```bash
          hugo new a.md
          ```
          (`a.md` is the name of the new post)  
        - Create a new post in a specific directory:  
          ```bash
          hugo new dir1/a.md
          ```
          (`dir1` is the target directory, posts in the same directory will be listed together)

    2.3 **Modify post front matter**  
        - To modify the default front matter for all posts, edit `archetypes/default.md`.

    2.4 **Modify front matter for a specific directory**  
        - Step 1: Create `dir1.md` in the `archetypes` folder (`dir1` is the target directory)  
        - Step 2: Edit `dir1.md` to adjust the front matter for all posts in that directory.

3. **Shortcodes**  
    - Example:  
      ```markdown
      {{< youtube sbHG1lwK7O4 >}}
      ```
      (`sbHG1lwK7O4` is the part of the YouTube URL after `v=`)

4. **Using tags and categories**  
    - In the front matter of a post's markdown file:  
      ```yaml
      tags: ["project", "work", "experiment"]
      categories: ["research"]
      ```
    - To add new taxonomies, add the following to `config.toml`:  
      ```toml
      [taxonomies]
        tag = "tags"
        category = "categories"
        mood = "moods"
      ```

5. **Adjusting list template**  
    - Create `_index.md` to create a list. Posts in the same directory will be listed together.  
    - To modify list template parameters, edit `list.html` in the theme's `layouts` folder.  
    - To design your own list template, create `_default/list.html` in the `layouts` folder.

6. **Adjusting single template**  
    - Similar to list template, create `single.html` in the `_default` subfolder of `layouts`.

7. **Homepage settings**  
    - Create `index.html` in the root directory of `layouts` for homepage settings.

8. **Section template**  
    - Determine which folder in `content` you want to adjust (e.g., `dir1`).  
    - Create a folder with the same name in `layouts` (e.g., `layouts/dir1`).

9. **Base templates**  
    - Base templates apply to all types of templates.  
    - Create `_default/baseof.html` in the `layouts` folder.  
    - Example:  
      ```html
      <html>
      <head>
          <meta charset="UTF-8">
          <meta name="viewport" content="width=device-width, initial-scale=1.0">
          <meta http-equiv="X-UA-Compatible" content="ie=edge">
          <title>Document</title>
      </head>
      <body>
          Top of baseof
          <hr>
          {{ block "main" . }}
          <!-- This part will change based on the page -->
          {{ end }}
          <hr>
          {{ block "footer" . }}
          This is the default baseof footer.
          {{ end }}
          <hr>
          Bottom of baseof
      </body>
      </html>
      ```

Feel free to copy and paste these revised codes into your markdown file. Let me know if you need any further assistance!



### variables in hugo


~~ embed a PDF file in a page on your Hugo website.
方法一：https://github.com/anvithks/hugo-embed-pdf-shortcode
方法二：https://discourse.gohugo.io/t/how-to-produce-a-link-to-pdf-file-under-post-folder/29226

##ZJ的总结
使用方法一，在markdown文件中使用以下shortcode: {{ < embed-pdf url="./2009.pdf" hidePaginator="true" > }} 
##其中，pdf文件具体放置的位置：使用该markdown文件的名字命名一个同样的文件夹
##（例如markdown文件为pub.md，则创建一个pub文件夹），然后将该pub.md页面中所有需要链接的文件都放在pub文件夹中。

##同样的操作也适用于方法二（重点是确定文件的正确地址，可以试着点击链接，然后在修改）


### 可能用到的index.html中的code
{{ define "main" }}
{{ .Title }}

{{ with .Params.subtitle }} {{ . }} {{ end }}
{{ .Content }}
{{ range first 10 .Site.RegularPages }} {{ .Render "summary" }} {{ end }}
{{ end }}


### how to push to repository through MAC terminal (CLI)

##### before you push, make sure no secrets (e.g., PATs) are in the codes

1. change directory to working folder in MAC terminal (使用 cd 命名)

2. Initializing a Git repository (https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github)
$ git init -b main

#使用PaperMod可能需要
$ git submodule update --init --recursive 
~~ needed when you reclone your repo (submodules may not get cloned automatically)

#add all files and commit
$ git add .
$ git commit -m "First commit"

3. Adding a remote repository （https://docs.github.com/en/get-started/getting-started-with-git/managing-remote-repositories#adding-a-remote-repository）
  e.g.: 
  $ git remote add origin https://github.com/zhangjunfelix/demopush.git
~~ Set a new remote

$ git remote -v
~~ Verify new remote
> origin  https://github.com/zhangjunfelix/demopush.git (fetch)
> origin  https://github.com/zhangjunfelix/demopush.git (push)

4. (通常第一次init，应该不会出现这个问题)
如果出现Remote origin already exists的报错信息，可以通过两种方法解决：rename 或者 remove 
(详见：https://docs.github.com/en/get-started/getting-started-with-git/managing-remote-repositories#removing-a-remote-repository)

$ git remote rm origin
~~remove已有的remote repo
~~重新增加remote repo

5. Pushing commits to a remote repository
$ git push origin main
此时，会提示输入密码。
如果需要输入github的密码pat

6. deploy via Github pages
[link to workflow](https://gohugo.io/hosting-and-deployment/hosting-on-github/)
follow the steps specified here

7. deploy via Netlify
#创建public
$ hugo 或者  $ hugo -D

#创建.gitmodules文件
$ touch .gitmodules
#在该文件中输入以下内容：
[submodule "themes/PaperMod"]
    path = themes/PaperMod
    url = "https://github.com/adityatelange/hugo-PaperMod.git"


###add, commit, push到github

#deployment
build command: hugo
https://gohugo.io/hosting-and-deployment/hosting-on-netlify/


####config.yml
params:
  homeInfoParams:
     Title: "Felix, a linguist"
     Content: Welcome to Felix's website!  Here you'll get to know my work as a linguist.
              This is Zhang Jun (张 zhāng  军 jūn in simplified Chinese)(張 jēung 軍 gwān in traditional Chinese). 
              Here you'll get to know me as a linguist. Anyone who wants to get in touch, please email me zhangjun-felix@hotmail.com      

  

  socialIcons:
    - name: github
      url: "https://github.com/"
    - name: facebook
      url: "https://facebook.com/"
    - name: instagram
      url: "http://instagram.com/"

  cover:
     linkFullImages: false
     
     
##_index.md文件
~~frontmatter
title: ""
date: 2023-07-06T22:37:08+08:00
draft: true

cover: 
   image: images/me.png
   caption: Me in the eyes of my dearest daughter Elsie

socialshare: true


### Welcome to Felix's website!  ### 
\
This is Zhang Jun (simplified Chinese: 张 zhāng  军 jūn)(traditional Chinese: 張[jēung]軍[gwān]). \
\
Here you'll get to know me as a linguist. 
\
\
Anyone who wants to get in touch, please email me: zhangjun-felix@hotmail.com




###Deploying a Blog Powered by Hugo to Github Pages w/ Custom Domain via Github Actions###

https://theplaybook.dev/docs/deploy-hugo-to-github-pages/


###deploy with NETLIFY过程中，如果遇到以下error
Module PaperMod is not compatible with this Hugo version; run hugo mod graph for more information.

add the following code to your config file
ignoreErrors: ["error-remote-getjson"]  #yml 
or 
ignoreErrors = ["error-remote-getjson"]  #toml 

source: https://github.com/adityatelange/hugo-PaperMod/discussions/615



###在markdown文件中加图片

例如：EAP.md文件中，插入EAP.jpg，可使用
![](/images/EAP.jpg "EAP")

###这里images前的"/"非常重要

Finally, here are some helpful tutorials.   
1. [Getting Started With Hugo | FREE COURSE](https://www.youtube.com/watch?v=hjD9jTi_DQ4&t=438s "Getting Started With Hugo")   
2. [Hugo tutorials by Giraffe Academy](https://www.youtube.com/watch?v=qtIqKaDlqXo&list=PLLAZ4kZ9dFpOnyRlyS-liKL5ReHDcj4G3)



*** Jekyll ***

