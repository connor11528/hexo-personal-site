# Create a custom blog theme with Hexo.js

[Hexo.js](https://hexo.io/) is an awesome blogging platform. If you have ever used Ruby's Jekyl it is like that but made of javascript! It is also open source and free to use.

![](http://gabijack.com/wp-content/uploads/2013/07/Javascript-AllTheThings.jpg)


### Generate a blog

```
$ npm install -g hexo-cli
$ hexo init hexo-personal-site
$ cd hexo-personal-site
$ npm install
$ hexo server
```

Go to `localhost:4000` and you will see the starter blog template! Very easy to get up and running. If you want to use a community build theme go to [github/hexo/wiki/themes](https://github.com/hexojs/hexo/wiki/Themes) and choose one from the list. Change line 66 of **_config.yml** to the name of the theme you want (default is 'landscape').

### Create your own template

> Hexo [themes docs](https://hexo.io/docs/themes.html)

We can create our own custom theme by making a new folder in the **themes/** directory. Change line ~68 in **_config.yml** to `theme: customTheme`, then create a **customTheme** folder in **themes**.

```
$ mkdir themes/customTheme
```

Now let's create the most basic theme possible.