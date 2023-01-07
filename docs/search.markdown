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
<script src="/docs/js/search-script.js" type="text/javascript"></script>

<!-- Configuration -->
<script>
SimpleJekyllSearch({
  searchInput: document.getElementById('search-input'),
  resultsContainer: document.getElementById('results-container'),
  searchResultTemplate: '<div><a href="{url}"><h1>{title}</h1></a><span>{date}</span></div><div><span>{content}</span></div>',
  json: '/docs/search.json'
})
</script>
