---
layout: page
title: Reading List
permalink: /reading-list/
---

# My Reading List

This page lists articles, books, and resources I want to read or have recently added to my list.

{% comment %}
Sort entries by 'date_added' in reverse order (most recent first).
{% endcomment %}
{% assign sorted_entries = site.data.reading_list | sort: "date_added" | reverse %}

<div class="reading-list">
  {% for entry in sorted_entries %}
  <div class="reading-item">
    <h3><a href="{{ entry.url }}" target="_blank" rel="noopener noreferrer">{{ entry.title }}</a></h3>
    <p><strong>Author:</strong> {{ entry.author }}</p>
    <p><strong>Added:</strong> {{ entry.date_added }}</p>
    <p><strong>Tags:</strong>
      {% for tag in entry.tags %}
        <span class="tag">{{ tag }}</span>{% unless forloop.last %},{% endunless %}
      {% endfor %}
    </p>
    
  </div>
  <hr>
  {% endfor %}
</div>

<style>
  /* Basic styling for your reading list */
  .reading-list {
    margin-top: 20px;
  }
  .reading-item {
    margin-bottom: 20px;
    padding: 15px;
    border: 1px solid #eee;
    border-radius: 8px;
    background-color: #121212;
  }
  .reading-item h3 {
    margin-top: 0;
    margin-bottom: 10px;
    font-size: 1.4em;
  }
  .reading-item p {
    margin-bottom: 8px;
    font-size: 0.95em;
  }
  .reading-item .tag {
    display: inline-block;
    background-color: #bb86fc; /* Light blue for tags */
    color: #333;
    padding: 4px 10px;
    border-radius: 5px;
    font-size: 0.75em;
    margin-right: 5px;
    margin-top: 5px;
    white-space: nowrap;
  }
  .btn {
    display: inline-block;
    padding: 8px 15px;
    background-color:rgb(5, 60, 118); /* Bootstrap primary blue */
    color: white;
    text-decoration: none;
    border-radius: 5px;
    transition: background-color 0.3s ease;
    font-size: 0.9em;
    margin-top: 10px;
  }
  .btn:hover {
    background-color: #0056b3;
  }
  hr {
    border: 0;
    height: 1px;
    background: #eee;
    margin: 30px 0;
  }
</style>