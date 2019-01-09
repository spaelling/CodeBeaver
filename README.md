## Welcome to my blog

This is a continuation of [codebeaver.blogspot.com](https://codebeaver.blogspot.com)

In some cases I may have ported a blogpost to here.

Happy reading!

## Posts

[PowerShell Modules in Azure Function App](/_posts/2019-01-09-PowerShell-Modules-In-Azure-Function-App.md)

{% for category in site.categories %}
  <h3>{{ category[0] }}</h3>
  <ul>
    {% for post in category[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}

### Posts by tag

Below is listed each post by tag

{% for tag in site.tags %}
  <h4>{{ tag[0] }}</h4>
  <ul>
    {% for post in tag[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}