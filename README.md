This repo contains a custom stylesheet for [Madek](https://github.com/orc-hfg/resources/wiki/Madek), a software at the intersection between an institutional repository and digital asset management. The stylesheet was developed by [Open Resource Center](https://hfg-karlsruhe.de/forschung-und-entwicklung/orc/), a project of Karlsruhe University of Arts and Design. 

The Madek WebApp is a complex application written in Ruby on Rails and React. To some, it might look a bit outdated nowadays. We felt the need to refresh the visual interface – with minimal expense. 

Our custom CSS stylesheet gets loaded after the regualr one so the defaults of Madek are extended or overwritten. In our case, we added two lines of code to the _base template to achieve this.

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