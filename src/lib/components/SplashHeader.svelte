<script>
  import { asset } from '$app/paths';

  let {
    kicker = '',
    headline,
    dek = '',
    byline = '',
    pubDate = '',
    backgroundImage = '',
    backgroundAlt = '',
  } = $props();

  const resolvedBackground = $derived(
    backgroundImage.startsWith('/') && !backgroundImage.startsWith('//')
      ? asset(backgroundImage)
      : backgroundImage
  );

  function formatDate(dateString) {
    if (!dateString) return '';

    const [year, month, day] = dateString.split('-').map(Number);
    const date = new Date(year, month - 1, day);

    return new Intl.DateTimeFormat('en-US', {
      year: 'numeric',
      month: 'long',
      day: 'numeric',
    }).format(date);
  }
</script>

<header class="splash-header">
  {#if backgroundImage}
    <img class="splash-image" src={resolvedBackground} alt={backgroundAlt} />
  {/if}

  <div class="splash-overlay"></div>

  <div class="splash-content">
    {#if kicker}
      <p class="kicker">{kicker}</p>
    {/if}

    <h1 class="headline">{headline}</h1>

    {#if dek}
      <p class="dek">{dek}</p>
    {/if}

    {#if byline || pubDate}
      <p class="meta">
        {#if byline}
          <span class="byline">By {byline}</span>
        {/if}
        {#if byline && pubDate}
          <span class="separator">•</span>
        {/if}
        {#if pubDate}
          <time datetime={pubDate}>{formatDate(pubDate)}</time>
        {/if}
      </p>
    {/if}
  </div>
</header>

<style>
  .splash-header {
    position: relative;
    width: var(--size-full);
    min-height: var(--story-cuny-splash-min-height);
    overflow: hidden;
    display: flex;
    align-items: flex-end;
    background: var(--story-cuny-hero-gradient);
    margin-bottom: var(--spacing-md);
  }

  .splash-image {
    position: absolute;
    inset: var(--spacing-none);
    width: var(--size-full);
    height: var(--size-full);
    object-fit: cover;
    opacity: var(--story-cuny-splash-image-opacity);
  }

  .splash-overlay {
    position: absolute;
    inset: var(--spacing-none);
    background: var(--story-cuny-hero-gradient);
  }

  .splash-content {
    position: relative;
    width: var(--size-full);
    max-width: var(--story-cuny-splash-content-width);
    color: var(--story-cuny-card-text);
    padding: var(--spacing-xl) var(--spacing-md);
    margin: var(--spacing-none) auto;
    text-shadow: var(--spacing-none) var(--spacing-none) var(--spacing-xs) var(--color-dark);
  }

  .kicker {
    font-family: var(--font-sans-ui);
    font-size: var(--font-size-sm);
    font-weight: var(--font-weight-bold);
    text-transform: uppercase;
    letter-spacing: var(--letter-spacing-wider);
    margin-bottom: var(--spacing-sm);
    color: var(--story-cuny-highlight);
  }

  .headline {
    font-family: var(--font-serif-display);
    font-size: var(--font-size-display);
    font-weight: var(--font-weight-bold);
    line-height: var(--leading-tight);
    margin-bottom: var(--spacing-sm);
    color: var(--story-cuny-paper);
  }

  .dek {
    font-family: var(--font-sans-ui);
    font-size: var(--font-size-lg);
    line-height: var(--leading-normal);
    margin-bottom: var(--spacing-md);
    color: var(--story-cuny-card-text);
    max-width: var(--story-cuny-splash-content-width);
  }

  .meta {
    display: flex;
    flex-wrap: wrap;
    gap: var(--spacing-xs);
    font-family: var(--font-sans-ui);
    font-size: var(--font-size-sm);
    letter-spacing: var(--letter-spacing-wide);
    color: var(--story-cuny-card-text);
  }

  .byline {
    font-weight: var(--font-weight-semibold);
  }

  .separator {
    color: var(--story-cuny-highlight);
  }
</style>
