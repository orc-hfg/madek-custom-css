Custom stylesheet for [Madek](https://github.com/orc-hfg/resources/wiki/Madek), developed by [Open Resource Center](https://hfg-karlsruhe.de/forschung-und-entwicklung/orc/), a project of Karlsruhe University of Arts and Design in 2024.

The custom CSS is loaded after the regular one so the defaults of Madek can be extended or overwritten. In our case, we added two lines of code to the _base template.

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


License: [GPLv3](https://www.gnu.org/licenses/gpl-3.0.html)