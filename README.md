# Web design for rails
How to style your site to show off your skills
## Setup
#### bootstrap
The folks at bootstrap have set up a really nice framework for any website. We are going to take advantage of their styles and grid features to get a big head start on designing our site. Start by adding bootstrap as a gem.
1. Add the bootstrap gem to your Gemfile then bundle. (You probably already have sass-rails installed)
```
gem 'bootstrap-sass'
gem 'sass-rails'
```

2. Change the name of application.css to application.scss, or application.sass, and import these
```
@import "bootstrap-sprockets";
@import "bootstrap";
```
you will need the semi-colon for .scss, but not for .sass
3. Add a reset file to your assets/stylesheets folder, and import it in application.sass just below bootstrap
```
@import 'reset';
```
I would just copy and paste one into a new file. [Here is a source.](https://github.com/jasonkarns/css-reset/blob/master/reset.css)
4. Remove everything from that sass file, and import your own sass files<br>
```
@import "yourfilename";
@import "yourotherfilename";
```

#### navigation
One of the most useful bootstrap features is the navigation. Let's put it in our view by making it a partial and placing it above the `<%= yield %>`
```
...
<%= render partial: "nav" %>
<%= yield %>
...
```
For our actual navigation, let's go the simplest route possible. We will use just a few bootstrap classes to define our navigation:
```
_nav.erb.html

<div class="navbar">
  <div class="pull-left">
    <img src="your_logo_filepath.jpg">
  </div>
  <div>
    <a class="navbar-nav">link text here</a>
  </div>
  <div>
    <a class="navbar-nav">link text here</a>
  </div>
</div>
```
`pull-left` and `pull-right` are handy classes that you can use anywhere to move content to the left or right side of its parent.

You can certainly use a ul for the navigation, but using divs may avoid any unexpected ul/li behavior.

Now would be a good time to add some CSS to make this navbar look the way we want it to. Make a new file in your assets/stylesheets folder called nav.sass
```
nav.sass

.navbar
  margin-right: 20px

.navbar-nav
  float: right
  padding: 20px 30px
  font-size: 16px
  color: white

.navbar-nav:hover
  color: white
  background-color: black

```
Don't forget to @import this file in your application.sass file.
#### footer
We can do a very similar thing for the footer. Lots of sites have dark gray footers with light text. I think that looks nice so that is what I am going to do, and in this case I've already defined a `$dkgray` in my `color.sass` file. I also make sure to give my footer a `min-hieght` so it shows up right away.

```
footer.sass

.footer
  margin-top: 30px
  min-height: 200px
  background-color: $dkgray
  padding: 20px
```
Don't forget to @import this file in your application.sass file.
## Font
#### Web fonts
[Google Fonts](https://fonts.google.com/) is free and easy to use. If you don't find any of those to your liking try [Adobe Typekit](https://typekit.com/). They host a ton of professional fonts, for a reasonable subscription fee.

I have had the best luck with linking to my Google fonts in the head of my application.html file. The @import method seems like it doesn't play nice with the server.
#### Serif vs. Sans-serif
Choose a sans-serif font for your headings, and a serif font for your body text. (You could also choose a sans-serif/sans-serif combo.) Pairing fonts can be a bit of a dark art, so let the pros do all the work for you. Check out [Font Pair](http://fontpair.co/) and choose a Google font combination that looks good to you.

I always err on the side of 'boring' when choosing a font. You don't really want the user to notice the font of your site, you just want it to work with the design.

If you want to dive even deeper into type, this is a great place to start. [Upping Your Type Game](http://jessicahische.is/talkingtype)
## Color

## Resources

* [coolors](https://coolors.co) Press the space bar to get 5 more colors
* [Kuler](https://color.adobe.com/) Adobe's tool for color. Click 'EPick a theme and Edit to customize.
* [Google Fonts](https://fonts.google.com/) Free web-hosted fonts
* [Font Pair](http://fontpair.co/) font combination resource for Google Fonts
* [Type Connection](http://www.typeconnection.com/) font-pairing game!
* [Adobe Typekit](https://typekit.com/) non-free web-hosted fonts
* [Upping Your Type Game](http://jessicahische.is/talkingtype) by Jessica Hische
