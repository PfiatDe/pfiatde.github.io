---
layout: page
title: Search
permalink: /search/
---

<!-- Html Elements for Search -->
<div id="search-container">
<input type="text" id="search-input" placeholder="search...">
<ul id="results-container"></ul>
</div>

<!-- Script pointing to search-script.js -->
<script src="/js/search-script.js" type="text/javascript"></script>

<!-- Configuration -->
<script>
SimpleJekyllSearch({
  searchInput: document.getElementById('search-input'),
  resultsContainer: document.getElementById('results-container'),
  searchResultTemplate: '<div><a href="{url}"><h1>{title}</h1></a><span>{date}</span></div><div class="container-lg px-3 my-5 markdown-body">{content}</div>',
  json: '/search.json'
})
</script>
