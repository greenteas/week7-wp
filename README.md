# Project 7 - WordPress Pentesting

Time spent: **X** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds (8768)
  - [ ] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.7.3
  - [ ] GIF Walkthrough: ![YouTube Embed XSS](https://raw.githubusercontent.com/greenteas/week7-wp/master/youtubeEmbedXSS.gif)
  - [ ] Steps to recreate: 
    - Go to add a new post or edit an existing post in Wordpress admin console in Text mode.
    - Embed a YouTube video with JavaScript within its URL, escaping the < and > characters.
    
    ```[embed src='https://youtube.com/embed/12345\x3csvg onload=alert(1)\x3e'][/embed]```
    - Return to Visual to preview the post. The alert should appear.
  - [ ] Affected source code:
    - [class-wp-embed.php](https://core.trac.wordpress.org/browser/branches/4.2/src/wp-includes/class-wp-embed.php)

2. Large File Upload Error XSS (8819)
  - [ ] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.7.5
  - [ ] GIF Walkthrough: ![Large File XSS](https://raw.githubusercontent.com/greenteas/week7-wp/master/largefileXSS.gif)
  - [ ] Steps to recreate: 
    - Create a large file over the upload limit for WordPress. (File made here is over 20MB)
    - Rename it as an image with JavaScript within its name in an img tag.
    ```apples<img src=a onerror=alert(1)>.png```
    - Go to Media (/wp-admin/media-new.php) in the admin console and upload the file.
    - The script should be executed when an upload error occurs because of the maximum file upload size.
  - [ ] Affected source code:
    - [script-loader.php](https://core.trac.wordpress.org/browser/branches/4.2/src/wp-includes/script-loader.php)

3. Unauthenticated Stored Cross-Site Scripting (XSS) (7945)
  - [ ] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.1
  - [ ] GIF Walkthrough: ![Large Comment XSS](https://raw.githubusercontent.com/greenteas/week7-wp/master/largecomment.gif)
  - [ ] Steps to recreate: 
    - Submit a very long comment on a post over 64 kB with JavaScript within it. Stretch the comment until it is 64 kB.
    ```<a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px AAAAAAAAAAAA [64 kb] ...'></a>```
    - When the mouse hover over the comment, the alert will appear.
  - [ ] Affected source code:
    - [comment.php](https://core.trac.wordpress.org/browser/branches/4.2/src/wp-includes/comment.php)

4. Authenticated Shortcode Tags Cross-Site Scripting (XSS) (8186)
  - [ ] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.5
  - [ ] GIF Walkthrough: ![Shortcode XSS](https://raw.githubusercontent.com/greenteas/week7-wp/master/shortcode.gif)
  - [ ] Steps to recreate: 
    - Make a post with the following code:
    
    ```[caption width='1' caption='<a href="' ">]</a><a href="onClick='alert(1)'">click for alert```
    - View the post and click the link.
  - [ ] Affected source code:
    - [kses.php](https://core.trac.wordpress.org/browser/branches/4.2/src/wp-includes/kses.php)
    - [shortcodes.php](https://core.trac.wordpress.org/browser/branches/4.2/src/wp-includes/shortcodes.php)

5. Authenticated Stored Cross-Site Scripting (XSS) (8111)
  - [ ] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.3
  - [ ] GIF Walkthrough: ![Shortcode XSS](https://raw.githubusercontent.com/greenteas/week7-wp/master/shortcode2.gif)
  - [ ] Steps to recreate: 
    - Make a post with the following code:
    
    ```<a href="[caption code=">]</a><a title=" onmouseover=alert('test')  ">link</a>```
    - View the post and hover over the link.
  - [ ] Affected source code:
    - [kses.php](https://core.trac.wordpress.org/browser/branches/4.2/src/wp-includes/kses.php)
    - [shortcodes.php](https://core.trac.wordpress.org/browser/branches/4.2/src/wp-includes/shortcodes.php)

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)
- [YouTube Embed XSS](https://blog.sucuri.net/2017/03/stored-xss-in-wordpress-core.html)
- [Large File XSS](https://hackerone.com/reports/203515)
- [Large Comment XSS](https://packetstormsecurity.com/files/131644/)
- [Shortcode XSS](http://blog.checkpoint.com/2015/09/15/finding-vulnerabilities-in-core-wordpress-a-bug-hunters-trilogy-part-iii-ultimatum/)
- [Shortcode/HTML Tag XSS](https://klikki.fi/adv/wordpress3.html)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [yyyy] [name of copyright owner]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
