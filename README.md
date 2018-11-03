# Project 7 - WordPress Pentesting

Time spent: **X** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds (CVE-2017-6817)
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

2. Large File Upload Error XSS (CVE-2017-9061)
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

3. (Required) Vulnerability Name or ID
  - [ ] Summary: 
    - Vulnerability types:
    - Tested in version:
    - Fixed in version: 
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)

4. (Optional) Vulnerability Name or ID
  - [ ] Summary: 
    - Vulnerability types:
    - Tested in version:
    - Fixed in version: 
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
5. (Optional) Vulnerability Name or ID
  - [ ] Summary: 
    - Vulnerability types:
    - Tested in version:
    - Fixed in version: 
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php) 

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)
- [YouTube Embed XSS](https://blog.sucuri.net/2017/03/stored-xss-in-wordpress-core.html)
- [Large File XSS](https://hackerone.com/reports/203515)

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
