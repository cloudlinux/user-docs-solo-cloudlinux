# AccelerateWP & Smart Advice

AccelerateWP is an improved and updated WP Optimization Suite.

## Introduction

Performance has a great impact on the site attendance and efficiency. We know that many customers want an auto tool to resolve problems with site performance. Many sites are built with WordPress CMS. So, we decided to find and implement a complex solution – the AccelerateWP tool to help our customers increase their site performance.

There are two modules in the AccelerateWP: Object Cache Module and Site Optimization Module.

The **Smart Advice** tool helps to decide which module will be most effective and helpful for particular website performance optimization.


### Object caching explanation

Caching is a mechanism of accessing frequently used data quickly. This mechanism is really helpful in case your site needs to process multiple pages per second as requests come in. If data is stored in cache the server does not need to process it time after time because such data can be obtained from the cache. So, visitors get it faster – it is really fantastic!

And one more interesting thing is that there are different types of caching.

* One type of caching is already used by your browser (client-side).
* And another type of caching (one of server-side) is used to store database queries data and is called the Object cache.

The speed of processing queries to the database is very important for WordPress CMS, because all content data is stored in the WordPress database. So, if you activate (turn on) the Object cache module it means that you activate some storage to cache queries from your clients to the WordPress database. Every time users of your site request some content for the web page it makes a request to the WordPress database.

### Our solution for the Object cache module

The solution is based on the Redis Object cache [https://wordpress.org/plugins/redis-cache/](https://wordpress.org/plugins/redis-cache/) and automatically sets up the Redis key-value storage and configures it appropriately.

The storage is located in the RAM of the server which stores data from the WordPress database queries. It caches objects between multiple page loads. But restarting the Object cache module daemon (very rare situation) will erase the data in the storage, and some period of time is needed to collect the data again.

When we recommend to use Object cache module:

* Websites used for extremely active exchange of information (forums, blogs, etc..)
* Websites with too many requests running at the same time
* Websites having important pages that cannot be cached entirely and exclude from the "whole page caching" due to any reason


#### How can we monitor the state of the Object cache module?

* Status of the storage (or Object cache database)
* Cache memory usage (or memory usage by the Object cache module)
* Max Memory usage limit (or limit for memory using by the Object cache module)


### Object Cache Module Limitations

For the first beta release, there are the following limitations:

* Required ea-PHP version 7.4 and 8.0.
* Recommended WordPress version 3.7 and higher.
* Object Cache module conflicts with other WordPress Caching plugins.
* Object Cache module conflicts with the [Snuffleupagus](https://snuffleupagus.readthedocs.io/) php-extension.
* Object Cache module does not work with WordPress Multisite mode.

### Site Optimization Module

Site Optimization Module incorporates best practices in improving website performance.

The main techniques which will be applied:

* Caching
* File optimization
* Media Lazy Load
* Content Preload 
* Database cleanup

### Smart Advice

How does Smart Advice make a decision which module needs to be activated?

Smart Advice has information about types of slow requests for the site for the appropriate period of time and creates new advice based on it. Advices are generated automatically so no additional configuration is needed.  


## AccelerateWP User Interface

1. Go to the list of software on your control panel and find the AccelerateWP icon:

![](/images/WPOptimizationSuiteIcon.png)

2. Open plugin interface

![](/images/WPPluginInterface.png)

3. You can turn on the Object Cache module or the Site Optimization module by yourself or via the Smart Advice suggestion.

### AccelerateWP information panel

On the AccelerateWP information panel you can find the following statuses.

* **Object Cache module Database status**

It will be offline if there is no sites using the Object Cache plugin.

![](/images/ObjectCacheModuleDatabaseStatus.png)

* **Amount of memory used by the Object Cache database**
  
![](/images/CacheMemoryUsage.png)

:::warning Attention!
In the first beta release this memory usage includes memory usage by the inner Object Cache plugin structures.
So, it cannot be zero.
:::

* **Limit for the Object Cache database**

![](/images/MaxCacheMemoryLimit.png)


Click on the ![](/images/EditLimitPen.png) to change the limit.

:::warning Attention!
There is the value limitation for the Max Cache Memory: from 16 MB to 16 GB.
:::

![](/images/CacheMemoryLimitation.png)

Use the ![](/images/PurgeAllCache.png) button to clear cache for all websites.

* **Smart Advice Suggestions**


### Manage Smart Advice

The advices are in the table:

![](/images/SmartAdviceTable.png)

To get an updated list of advices, click the *Refresh advice* button.

A **not applied advice** has the *Review* status, description of suggesting optimization and the *Turn on site optimization* button.

![](/images/NotAppliedAdvice.png)

An applied advice will not disappear from the AccelerateWP interface, but it will be in the *Applied* state.

![](/images/AppliedAdvice.png)
	

### Object Cache Module error messages

#### No compatibility message

Causes of the "No compatibility" message are always [Limitations](/wpos-plugin/#object-cache-module-limitations). Each message has a small "how to", so you can try to fix them by yourself via cPanel or WordPress Admin interface.

![](/images/WPNoCompatibility.png)

#### Misconfiguration message

The misconfiguration message can appear in the following cases:

* Redis process cannot be started for some period of time. **Resolution**: [contact our support team](https://cloudlinux.zendesk.com/hc/en-us/requests/new) for further investigation.
* WordPress Redis Object Cache plugin is disabled via WordPress Admin Gui/Plugins. **Resolution** You can resolved it by yourself via the WordPress Admin Gui.
* Version of PHP is incompatible or does not have all needed modules installed.

![](/images/WPMisconfiguration.png)

#### Post check issues

If you have some Post check issue after turning On the Object Cache module, you can leave them as disabled (in that case the engine reverts all changes). Or you can ignore the issue and continue working with the enabled Object Cache module.

#### General errors and warnings during activation plugin

If you get something like "Unexpected WordPress error" you can do the following:

![](/images/UnexpectedError.png)

* As the first step, verify that [Limitations](/wpos-plugin/#object-cache-module-limitations) are not broken.
* As the second step, [contact our support team](https://cloudlinux.zendesk.com/hc/en-us/requests/new) for further investigation.

### Site Optimization Module Settings

You can find the CloudLinux Site Optimization plugin in the WordPress Admin interface.

![](/images/OptimizationModuleUI.png)


Open *Settings*.

![](/images/OptimizationSettings.png)

#### Caching

#### Mobile caching 
 
Use it only if you website is adapted to use on smartphones and mobile phones.

Separate cache files for mobile devices. In this case the content for mobile devices will be cached into different cache file as for desktop\tablets.

This option is necessary if you have some functionality only for mobile devices, not for desktop\tablets.

When use such options.

![](/images/CacheUsageOptions.png)

:::tip Note
If you use an additional layer of Cache (Varnish, NGINX , etc.) make sure it can distinguish between desktop and mobile visitors.
:::

#### User Cache

It is recommended to use such an option when your website has a unique content for each logged-in user. If the user is not logged-in, a common site cache will be used, otherwise each logged-in user’s content will be cached separately.

#### File Optimization

File Optimization consists of Minification and file Combining.

Minification is the process of minimizing code in your web pages and script files. Webmasters look at minification as a primary method of reducing website load times via the bandwidth they use.

Minification also reduces JS, CSS and HTML files. The goal is removing comments and extra spaces. It crunches variables that minimize code and ultimately reduces the file size. 

After minification, the file still functions as it should. The difference is a reduction in bandwidth due to network requests.

**By combining CSS & JS files, HTTP/1 does not allow multiple requests from the same TCP connection between a host server and a web browser**. 

Putting CSS and JS files into their respective groups, makes requests for downloads from a browser safe and more efficient. The old way meant multiple connections that took up bandwidth. 
 
**File (CSS & JS) combining is not necessary for HTTP/2** (see [https://webspeedtools.com/should-i-combine-css-js/](https://webspeedtools.com/should-i-combine-css-js/))

HTTP/2 introduced multiplexing. Now, the browser can send unlimited number of requests to the server, then download all files simultaneously with only one TCP connection.

Consequently, HTTP/2 takes care of multiple TCP connections and the waiting times before each download. In one sense, consolidating CSS and JS files might be unnecessary. 
 
To verify which HTTP version is used for requests on your site, you can use [https://tools.keycdn.com/http2-test](https://tools.keycdn.com/http2-test).

#### CSS Files

**Minify CSS**

Minify CSS reduces file sizes by taking out white space and comments embedded in the code. 

**Combine CSS**

Combine CSS reduces HTTP requests by merging all your files into one. Combine CSS is not recommended if your site uses HTTP/2. 

**Excluded CSS Files**

To single out those CSS files that should not be minimized, list the URLs attached to the CSS files that should be excluded from minification and concatenation (one per line).
 
:::warning Caution!
Minification removes the domain from the URL.
:::
 
To prevent that, use (. *).CSS wildcards to exclude all files in a specific location.
 
3rd Party: when excluding external CSS files, use the domain or the full URL path.

#### JavaScript Files

**Minify javascript files**

Minify JavaScript removes whitespace and comments to reduce the file size.

**Combine JavaScripts files**

This option will be active only if you choose Minify javascript files. It is not recommended for HTTP2.

**Load JavaScript deferred**

One major cause of slow web pages is a so-called blocking script ([https://www.dummies.com/web-design-development/javascript/deferred-loading-with-javascript/](https://www.dummies.com/web-design-development/javascript/deferred-loading-with-javascript/)).

Loading JavaScript called a blocking script blocks the webpage from loading.
 
Using the `defer` attribute alerts the browser not to wait for the script. Things will continue as usual per the build HTML and DOM processes. Quietly, the script rests in the background, then runs once the DOM is built.

So, the `Load JavaScript deferred` option adds to each script tag the `defer` attribute. 

**Delay JavaScript Execution**

This option helps to decrease the page load time by delaying loading of all JavaScripts on the page. This option can be applied only for already cached pages, it is incompatible with the Combine JavaScripts files option.

#### Media

**LazyLoad**

LazyLoad affects the page in the next way - if the user opens the page for the first loading there will be only first displayed (visible to user) images, others will be loaded if the user scrolls down. Images added via CSS file, the `<style>` tag or via `Elementor` will not be affected by the LazyLoad.

The following options allows working with LazyLoad

* Enable LazyLoad for images
* Enable LazyLoad for iframes and videos
* Excluded images or iframes

#### Image Dimensions

**Add Missing Image Dimensions**

Correct image dimensions help the browser to recognize page structure without delays, because the browser knows how much space is needed for the image.

Cases when image will not be affected by the *Add Missing Image Dimensions*:

* Images which have any attribute with name containing `*height*` or `*width*`
* Images which are part of the `<picture>` tag
* SVG images
* Image from external domains

#### Preload

**Preload Cache**

Usually, a page cache is created when this page is first visited. You can activate the preload page cache. It means that the cache for the page will be created when the page is created or updated.

If sitemap-based cache preloading is activated, a specified sitemap file will be used for preliminary cache generation.

**Preload Links**

Provides functionality to preload the HTML content of the hovered link for acceleration loading pages after click.

**Prefetch DNS Requests**

If your website uses external resources (e.g. Google fonts, Youtube video, etc) CloudLinux Site Optimization can preload these resources for accelerating loading pages. To activate preloading external URLs, provide a list of external URLs.

**Preload Fonts**

Accelerates the loading of fonts by the browser, informing the browser at the very beginning of the request about the full list of fonts to download

#### Advanced Rules

Advanced site caching settings. If you have specific pages that must be processed individually you can add a custom rule for them.

**Never Cache URL(s)**

Provide a list of URLs that cannot be cached.

**Never Cache Cookies**

Provide a list of Cookie files that cannot be cached.

**Never Cache User Agent(s)**

Provide a list of User Agent names that cannot be cached.

**Always Purge URL(s)**

You can specify URLs that will be deleted from the cache when any post or page will be updated.

**Cache Query String(s)**

By default CloudLinux Site Optimization does not cache URLs with query strings, but in this option, you can specify GET-parameters that must be cached.

#### Database

Database optimization provides clearing database from expired and unused data.

**Post Cleanup**

Provides clearing posts revisions, autosaved drafts, and deleted posts from the trash. Be careful, you will not be able to restore this data after clearing it.

**Comments Cleanup**

Provides clearing spam and deleted comments from the trash. Be careful, you will not be able to restore this data after clearing it.
 
**Transients Cleanup**

Provides clearing temporary options for existing plugins and older unused options that keep after deleting plugins.
 
**Database Cleanup**

Provides table optimizations in your database server.

**Automatic cleanup**

Allows you to schedule periodic database cleanups.

#### Heartbeat

WordPress Heartbeat is a function of server polling that provides delivery data from server to browser periodically.

**Reduce or disable Heartbeat activity**

To control server loads you can activate the *Control Heartbeat* function and reduce or disable Heartbeat activity. You can manage Heartbeat activity separately for backend, frontend, and post-editing parts. Be careful, disabling Heartbeat can break plugins that use this functionality.

#### One-click CloudLinux Site Optimization Add-ons

**Varnish**

When the server uses Varnish, you need to activate the add-on for implementing clearing Varnish cache when CloudLinux Site Optimization clears site cache.

**WebP Compatibility**

If your site uses the WebP plugin you can activate CloudLinux Site Optimization WebP Compatibility add-on to achieve browser compatibility with your WebP images.

#### Cloudflare

If your site is connected to the Cloudflare CDN you can activate the Cloudflare add-on to manage Cloudflare options with CloudLinux Site Optimization and automatic clearing cache when CloudLinux Site Optimization clears site cache. After activating the add-on, you need to click the *Modify Options* button and specify the Cloudflare API key, Account E-mail and Zone ID.


#### Tools

For backing up the settings, there is a function for exporting settings. To use it, click the *Download settings* button. When you need to restore settings, choose your saved settings file and click the *Upload file and import settings* button.


### Object Cache module Known Issues

1. If you open the WordPress admin panel and find Redis Object cache plugin, open Settings for it, you can find the following:

**Port: 6379**

It is incorrect (will be fixed soon), it works via the **file socket**.

2. If you get the following error:

![](/images/WPOSError1.png)

Try again later. The cause of the problem is a DDoS protection for the WP Optimization suite which allows restart daemon only once in a minute.


## FAQ

### How to measure the speed of the website?

You can measure the speed of your website before turning On the Object Cache module and after.

The popular tools:

* [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)
* [Pingdom Website Speed Test](https://tools.pingdom.com/)

### Where the AccelerateWP tool log files are located?

Login via SSH, find in your home directory  `~/.clwpos/main.log`. Or you can open it using the control panel file manager.

### I already use the WordPress Redis object cache plugin. Will the AccelerateWP be useful for me?

No, in the current version we suggest the same optimization as you already have. But we include other useful modules in the next versions, so let’s stay in touch.

### I already use the WordPress Redis object cache PRO plugin. Will the AccelerateWP be useful for me?

No, in the current version we suggest the same optimization as you already have. But we include other useful modules in the next versions, so let’s stay in touch.

### What is the difference between Object Module Cache and Caching in Site Optimization Module?

Object Cache Module - object caching in PHP code, only those objects that explicitly use the WordPress Object Cache are cached ([https://developer.wordpress.org/reference/classes/wp_object_cache/](https://developer.wordpress.org/reference/classes/wp_object_cache/)). Typically, such a cache is used to obtain the results of SQL queries or other code entities (some instances of classes, data arrays, etc.), i.e. it's more low-level caching. The page with such caches is also assembled from components, but some of them are taken from the cache if the cache is found in Redis.

Site optimization module - the entire page is cached and stored in the file system in the cache folder. At the very beginning of the request, the content of the file is read from the cache and sent to the user's browser. If there is a cache for the current page, it prevents the WordPress core part from loading, and all plugins, themes, and so on.