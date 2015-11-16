# Debugging in Drupal 8
Note:
- KG
- Hello Everyone! We are going to talk about "Debugging in D8"



## Slides
[bit.ly/pain-points-slides](http://bit.ly/pain-points-slides)

Note:
I have posted slides with speaker notes online and bit.ly
link for this session is. You can follow along the slides.




## Kalpana Goel

<a href="https://www.drupal.org/u/kgoel"><i class="fa fa-drupal"></i> kgoel</a>

<a href="https://twitter.com/kalpanagoel"><i class="fa fa-twitter"></i> kalpanagoel</a>

Note:
- KG
- Developer at Forum One
- Forum One is full service digital agency and does lot of work in Drupal for
Government and non-profit organizations.




<!-- .element: class="heading" -->
<!-- .slide: data-background="custom/images/09September_1.jpg"  data-state="show-header" data-header="" -->
## First mention of bug and debugging
<!-- .element: class="heading" -->

Note:
- KG
- First reported bug in 1947
- Bug and debugging terms are attributed to Grace Hopper when she was working on computer at Harward University.
- Someone discovered moth stuck and stop the operation, she made a remark that they are debugging the system 
- and since then we are using that term.





## Debugging steps 
Note:
- Write tests so there are minimal chances of bug in your code
- if a bug does exist, reproduce a problem
- use debug in your code. In D7 - var_dump(), dpm
- find the source of the problem and fix it.





## Debugging in Drupal 8
Note:
- 





## <!-- .slide: data-background="custom/images/website_error.png" data-background-size="" data-state="show-header" data-header="" -->
Note:
- If you see this sort of error (in my case long back while installing standard installation)
- doesn't give much information about error




### Enable Error Messages
## $config['system.logging']['error_level'] = 'verbose';
Note:
- examples.settings.local.php to settings.local.php, Uncomment lines in settings.php referring to settings.local.php 
 and uncomment the following the bottom of the file
- this turns CSS/JS aggregation off if you enable it
- Take a look in settings.local.php for in-depth documenation




## www.drupal.org/node/2313059
Note:
- No error shown by default
- NR would be great




## Runtime Assertions
Note:
- Assertions should be used only for debugging.
- Assertion is a true-false expression which is always expected to be true
- If an assertion is ever FALSE it indicates an error in the code



### Disable Dynamic Page Cache
## $settings['cache']['bins']['dynamic_page_cache'] = 'cache.backend.null';





### Disable Render Cache
## $settings['cache']['bins']['render'] = 'cache.backend.null';
Note:
- uncomment from settings.local.php
- drush cr
- Explain why? if you have a piece of content and if you want to make a change in the node
or block twig template, to display the changes then you would need to clear the cache all the time
if you don't want to do that then disable render cache. 
- Render caching enable by default to speed up page load
- Since we are talking about twig templates, lets talk about debugging in Twig
 




## Twig debugging
Note:
- Drupal8 uses Twig as its templating engine 
- services.yml (turn on settings for enabling twig debugging is in services.yml)
- if not cp sites/default/default.services.yml to services.yml





## How to enable debugging
 <code>parameters:
  twig.config:
    debug: true </code>
Note:
- enable twig debugging





## Benefits of enabling debugging in Twig
Note:
- Default: false
- dump() output template variables
- template file name suggestions - make it different slide to show it
- Turn off in production
- It enables auto-reload




## Template file name
<img src = "custom/images/template_file.png">
Note:
- Twig template file name suggestions are in order from most specific to least specific
- current file name suggestion in use has an "x" beside it
- Along with the BEGIN OUTPUT and END OUTPUT you will find the full path to the template being rendered




## Twig auto-reload
Note:
- This is another benefit of enabling Twig debug option
- automatically recompile Twig templates if source code changes
- Turn off in production
- look in services.yml file to read more about it





## Twig cache
Note:
- Its bad to disable twig cache
- don't touch it




## knit
Note:
- may be already familiar with knit
- It's way better than dump()
- knit module is sub-module of devel module which you can use as a debugging tool. you can use it from php or twig template.




## Console






## Web-profiler
Note:
- useful for debugging, performance testing
- learn how your site handles request
- Symfony 2 comes with WebProfiler bundle. It collects information about each request made to your site
- Allows to visualize in the browser
- WebProfiler is now a sub-module of devel



## WebProfiler in browser
<img src = "custom/images/webprofiler.png">
Note:
- Download devel module
- enable devel and webprofiler module
- clear cache
- Set the permission




## PHP Config
<img src="custom/images/php_config.png">
Note:
- Details about PHP version, enabled extensions




## Request Info
<img src = "custom/images/request_info.png">
- Info related to page request example - route matched, route object, request header, cookies




## Timeline
<img src="custom/images/timeline.png">
Note:
- Allows to visualize the order in which PHP controllers and events are called and time to compile them.
- Helps debug slow page load




## Performace Timing
<img src="custom/images/performance_timing.png">
Note:
-




## Database
<img src="custom/images/database.png">
Note:
- queries are listed in execution order with ability to search by filter (select, insert)
- or filter by slow query
- displays execution time, PHP file that made query
- EXPLAIN, INFO and SWAPPLACEHOLDERS



## User
<img src="custom/images/user.png">
Note:
- Name of current user
- roles etc. Provider?





## Views
Note:
- Displays list of views that was rendered on the current page




## Forms
Note:
- Lists forms built on the current page




## Extensions
Note:
- Displays all the modules and themes that are enabled on the site




## Cache
<img src="custom/images/cache.png">
Note:
- Displays different caches by ID and the number of hits/miss




## Assets
Note:
- Provides list of all CSS and JS files that were loaded for the page request




## <video data-autoplay src="custom/images/webprofiler_video.mov"></video>




## Thank You!
## Don't forget to rate session


