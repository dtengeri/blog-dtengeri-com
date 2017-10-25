---
title: How to use jQuery 1.4 in a Drupal 6 module
layout: post
tags: drupal jquery javascript
---

Welcome to my first blogpost!

I'm working on a project, where we need to use jQuery 1.4 and jQuery UI 1.8 in a Drupal 6 module. Unfortunately, the jQuery Update module only allows us to use 1.3.2 and we can only develop with the 1.6 version of jQuery UI by using the jQuery UI module.

It will break some of the Drupal core's and modules functionality if you simply replace the old jQuery source with the new one. There is a bug somewhere in the code of Drupal.
There are several patches, which fix this bug, but they are modifying the core's code. If you update your Drupal, you have to apply the patches again. To avoid this, we needed a solution, to use two versions of the jQuery together.

I want to explain how can you do this:

You will need two javascript files and you have to load the javascript files in the correct order.
The files you will need:
* init_level_1.js
* init_level_2.js

The content of init_level_1.js:

```javascript
var jQueryOriginal = $.noConflict(true);  
```

We use the jQuery's noConflict method, which will remove jQuery variables from gobal scope (including jQuery itself). We save the old jQuery object in a variable, because we will restore it later.

The content of init_level_2.js:

```javascript
//Save the new jQuery.  
var newjQuery = $.noConflict(true);  
//Restore the original one.  
jQuery = jQueryOriginal;  
$ = jQuery;  
```

Here we do the same as before. We save the new jQuery object and restore the old one. But from where do we get this new jQuery? This is the trick.
We have to load the javascript files in the following order:

```php
$path = drupal_get_path('module', 'your module');  
//Save old jQuery  
drupal_add_js($path .'/init_level_1.js');  
//Add the new jQuery  
drupal_add_js($path .'/jquery.1.4.2.min.js');  
drupal_add_js($path .'/jquery.ui.1.8.5.min.js');  
//Add plugins you want to use with the new version of jQuery will need  
...  
//Save the new jQuery and restore the original one  
drupal_add_js($path .'/init_level_2.js');
//Add your JS files after this
```

When you load the jQuery library, it will create the global jQuery object again, which will be saved in the init_level_2.js. You can add your JS files after init_level_2 and you have to write your JS code in the following style:

```javascript
(function ($) {  
   // You can use all of the features of jQuery 1.4 and jQuery UI 1.8 in this scope by using  
   // the $ variable.  
 })(newJquery); 
```

I hope this howto was useful. Happy coding!