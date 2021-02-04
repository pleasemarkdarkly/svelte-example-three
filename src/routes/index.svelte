<script context="module">
  export async function preload(page, session) {
    const res = await this.fetch(`index.json`);
    const response = await res.json();
    return response;
  }
</script>

<script>
  import Posts from '../components/Posts.svelte';
  import Breadcrumb from '../components/Breadcrumb.svelte';

  export let posts;
  export let postsPerPage;
</script>

<style lang="scss">
  .hero-section {
    padding: 10rem 2rem;
    font-size: 2rem;
    max-width: 700px;
  }
  h1 {
    font-weight: 600;
    font-size: 4rem;
    line-height: 4.5rem;
  }
  @media (max-width: 767px) {
    .hero-section {
      padding: 5rem 0;
    }
    h1 {
      font-size: 3rem;
      line-height: 3.5rem;
    }
  }
</style>

<svelte:head>
  <title>Mr. Whisker approves this Blog</title>
</svelte:head>

<div class="hero-section">
  <h1>CompuGlobalHyperMegaCorp Approved Blog Theme</h1>
  <p>"Easy as licking your butthole." Mr. Whiskers</p>
</div>

<Posts {posts} limit={postsPerPage} />

<Breadcrumb isFirst={true} isLast={postsPerPage > posts.length} page="1" />
