---
layout: page
title: Books
description: Book reading progress, reviews and recommendations
---

<style>
    li {
        margin-bottom: 5px;
    }
</style>

## Current Reading:
{% assign currentBooks = site.data.books | where: "isCurrent", true %}
{% for book in currentBooks %}
* [*{{ book.title }}*{% if book.author %} by {{ book.author }}{% endif %}]({{ book.link }}){:target="_blank"}
{% if book.summary %}  * {{ book.summary }}{% endif %}
{% endfor %}

## Read:
{% assign pastBooks = site.data.books
        | where_exp: "item", "item.completeDate < 2023"
        | sort: "title"
%}
{% for book in pastBooks %}
* [*{{ book.title }}*{% if book.author %} by {{ book.author }}{% endif %}]({{ book.link }}){:target="_blank"}
{% if book.rating %}  * My rating: {{ book.rating }}{% endif %}
{% if book.summary %}  * Summary: {{ book.summary }}{% endif %}
{% endfor %}

## To Be Read:
{% assign todoSorted = site.data.books
        | where_exp: "item", "item.isCurrent != true"
        | where_exp: "item", "item.completeDate == nil"
        | sort: "title"
%}
{% for book in todoSorted %}
* [*{{ book.title }}*{% if book.author %} by {{ book.author }}{% endif %}]({{ book.link }}){:target="_blank"}
{% if book.summary %}  * {{ book.summary }}{% endif %}
{% endfor %}
