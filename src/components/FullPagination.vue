<template>
  <nav class="pagination is-centered" role="navigation" aria-label="pagination">
    <a class="pagination-previous">Previous</a>
    <a class="pagination-next">Next page</a>
    <ul class="pagination-list">
        <li><a class="pagination-link" aria-label="Goto page 1">1</a></li>
        <li><span class="pagination-ellipsis">&hellip;</span></li>
        <li><a class="pagination-link" :aria-label="'Page' + current">45</a></li>
        <li><a class="pagination-link is-current" :aria-label="'Page' + current" aria-current="page">{{current}}</a></li>
        <li><a class="pagination-link" aria-label="Goto page 47">47</a></li>
        <li><span class="pagination-ellipsis">&hellip;</span></li>
        <li><a class="pagination-link" :aria-label="'Goto pages' + info.pages">{{info.pages}}</a></li>
    </ul>
</nav>
</template>

<script>
export default {
    props: ['info','current']
}
</script>

<style>

</style>