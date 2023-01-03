---
layout: page
title: Books
description: Book reading progress, reviews and recommendations
---

<style>
    li {
        margin-bottom: 5px;
    }

    /* non-existent days - MonthNum+1 */
    /* feb */
    table tbody tr:nth-child(29) td:nth-child(3), /* jekyll code to make conditional if leap year? lol */
    table tbody tr:nth-child(30) td:nth-child(3),
    table tbody tr:nth-child(31) td:nth-child(3),
    /* apr */
    table tbody tr:nth-child(31) td:nth-child(5),
    /* jun */
    table tbody tr:nth-child(31) td:nth-child(7),
    /* aug */
    table tbody tr:nth-child(31) td:nth-child(10),
    /* nov */
    table tbody tr:nth-child(31) td:nth-child(12) {
        background-color: #cccccc;
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
        | where_exp: "item", "item.completeDate < 2022-12-12"
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
