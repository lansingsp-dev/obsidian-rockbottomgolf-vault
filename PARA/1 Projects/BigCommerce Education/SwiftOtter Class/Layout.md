- `templates/layout/base.html `- 
	- Main layout html file that injects the following component html files
	  ```handlebars
		{{> components/common/header }}  
		{{> components/common/body }}  
		{{> components/common/footer }}
```
- `components/body.html` contains the `{{#block "page"}} {{/block}}` where the `{{#partial "page"}}` gets injected. Every html file under `template/page` surrounds the main page content as follows and will get injected into the body.html.
  
  blog.html
  ```handlebars
{{#partial "page"}}  
  
{{> components/common/breadcrumbs breadcrumbs=breadcrumbs}}  
  
<main class="page">  
    {{#unless theme_settings.hide_blog_page_heading }}  
        <h1 class="page-heading">{{ blog.name }}</h1>  
    {{/unless}}  
  
    {{#each blog.posts}}  
        {{> components/blog/post post=this theme_settings=../theme_settings}}  
    {{/each}}  
  
    {{> components/common/paginator pagination.blog}}  
</main>  
  
{{/partial}}
```
- 