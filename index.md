---
layout: page 
title: Hi, I am babacry! 
tagline: Supporting tagline
---
{% include JB/setup %}
- UPDATE MYSELF HERE.  
- DO SOME PROFESSIONAL/OTHER READINGS HERE.   
- RECORD SOME INTERESTING THINGS HERE.  
- MAY BE SOME THINKING HERE.  
- WHATEVER, BE MYSLEF, BE FREE...  
[ABOUT ME]({{ site.url }}/about.html)   

## Recent Articles  

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>


