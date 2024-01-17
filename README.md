## What 
This repo contains a custom stylesheet for [Madek](https://github.com/orc-hfg/resources/wiki/Madek), a software at the intersection between an institutional repository and digital asset management. The stylesheet was developed by [Open Resource Center](https://hfg-karlsruhe.de/forschung-und-entwicklung/orc/), a project of Karlsruhe University of Arts and Design. 

## Why
The Madek WebApp is a complex application written in Ruby on Rails and React. To some, it might look a bit outdated nowadays. We felt the need to refresh the visual interface – with minimal expense. 

## How 
We hook a custom CSS file into the Madek-WebApp, right after the regual CSS file gets loaded. The sequence is important, because our custom rules should extend or override the existing ones.

To do this, you need to add two lines of code and deploy the application:

`madek-webapp/app/views/layouts/_base.haml`

```haml
[...]

-# regular stylsheet
= stylesheet_link_tag 'application', media: 'all'
= content_for(:style_head)

-# our custom stylesheet
= stylesheet_link_tag '/assets/hfg-customization.css', media: 'all'
= content_for(:style_head)

[...]
```

You may also need to make changes to the web server, depending on your configuration. In our workflow, the CSS is located in a specific folder, to which a frontend-designer has access via SSH. We create an alias to that folder and grant access.  
Also, we need to make sure, the web browser doesn't cache our CSS. But this might differ or be left out completely, depending on your config file.

```Apache
[...]

Alias /assets/hfg-customization.css /home/custom-css/hfg-customization.css
<Directory /home/custom-css>
    Require all granted
</Directory>
<LocationMatch "^/assets/.*$">
    FileETag MTime Size
    ExpiresActive Off
</LocationMatch>

[...]
```