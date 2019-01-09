## Welcome to my blog

This is a continuation of [codebeaver.blogspot.com](https://codebeaver.blogspot.com)

In some cases I may have ported a blogpost to here.

Happy reading!

## Posts

[PowerShell Modules in Azure Function App](/_posts/2019-01-09-PowerShell-Modules-In-Azure-Function-App.md)

### Posts by theme

Below is listed each post by theme

{% for category in site.categories %}
  <h4>{{ category[0] }}</h4>
  <ul>
    {% for post in category[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}