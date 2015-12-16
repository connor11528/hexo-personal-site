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

Now let's create the most basic theme possible. We are using the EJS template engine, so make three files in the **themes/customTheme/layout** folder. One is called **layout.ejs**:

```
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<!-- Use <%= page.title %> for dynamic title -->
	<title><%= config.title %></title>

	<!-- Twitter bootstrap (via cdn) -->
	<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css" integrity="sha384-1q8mTJOASx8j1Au+a5WDVnPi2lkFfwwEAa8hDDdjZlpLegxhjVME1fgjWPGmkzs7" crossorigin="anonymous">

</head>
<body>
	<div class='container'>
		<%- body %>
	</div>
</body>
</html>
```

So here we're grabbing twitter bootstrap and setting the page title. The blog will render in the body tag.

The next file is **index.ejs** and it will be the home page:

```
<div class='row text-center'>
	<h1><%= config.author %></h1>
    <p><%= config.subtitle %></p>

</div>
<div class='row'>
	<ul>
	<% page.posts.each(function(post){ %>
    	<li>
    		<h3>
                <a href="<%- url_for(post.path) %>">
        			<%= post.title %>
        		</a>
            </h3>
            <div class='text-muted'>
                <%= date(post.date, config.date_format) %> 
            </div>
            
            <% if(post.excerpt) { %>
                <p>
                    <%- post.excerpt %>
                </p>
            <% } %>
    	</li>
  	<% }) %>
	</ul>
</div>
```

The `config` variable comes from everything we set in **config.yml**. The `<%-` syntax comes directly from [EJS syntax](https://github.com/tj/ejs). To see a post.excerpt add `<!-- more -->` to line 5 (or anywhere) in **source/_posts/hello-world.md**. To create a new post do `$ hexo new "My Post Title"`.

Finally there is the page where the post must render. Create **themes/customTheme/layout/post.ejs**:

```
<div class='row'>
	<a class='btn btn-default' href='/'>< Home</a>
</div>
<div class='row'>
	<h1><%- page.title %></h1>
	<div class='text-muted'>
        <%= date(page.date, config.date_format) %> 
    </div>
	<%- page.content %>
</div>
```

Here we make use of the `page` variable, which contains our post.

### Conclusion

This is a very basic template. There is a lot to learn with Hexo but it is a very powerful, customizable platform. You can pick from an existing theme or continue to develop off this one. The source code for this article is on [github](https://github.com/cleechtech/hexo-personal-site).


