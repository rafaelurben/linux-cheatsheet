---
---

<style>
    #search-input {
        border-top-left-radius: 0.25rem;
        border-bottom-left-radius: 0.25rem;
        border: 1px solid #1E6ADD;
    }

    #results-container {
        padding-top: 15px;
    }
</style>

<!-- Search form -->

<div class="input-group md-form form-sm form-2 pl-0">
    <input id="search-input" class="form-control my-0 py-1" type="text" placeholder="Suchen..." aria-label="Search">
    <div class="input-group-append">
        <span class="input-group-text red lighten-3" id="basic-text1">
            <i class="fas fa-search text-grey"
            aria-hidden="true">
            </i>
        </span>
    </div>
</div>

<ul id="results-container" class="list-group">
</ul>

<script src="https://unpkg.com/simple-jekyll-search@latest/dest/simple-jekyll-search.min.js"></script>

<script>
    SimpleJekyllSearch({
        searchInput: document.getElementById('search-input'),
        resultsContainer: document.getElementById('results-container'),
        searchResultTemplate: '<li class="list-group-item"><span><a href="{url}">{title}</a></span></li>',
        noResultsText: '<li class="list-group-item">No results found!</li>',
        fuzzy: false,
        limit: 25,
        json: '/search/content.json'
    });
</script>
