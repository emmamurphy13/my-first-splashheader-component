<!--
@component
This is your page!
-->
<script>
  // Import all the news furniture components
  import SplashHeader from '$lib/components/SplashHeader.svelte';
  import ArticleBody from '$lib/components/ArticleBody.svelte';
  import Image from '$lib/components/Image.svelte';
  import RelatedLinks from '$lib/components/RelatedLinks.svelte';
  import Dashboard from '$lib/components/Dashboard.svelte';
  import BigNumber from '$lib/components/BigNumber.svelte';

  // Article metadata
  let headline = 'Become a force for good. Join our next class.';
  let byline = 'NYCity News Service';
  let pubDate = '2026-01-31';
  let dek = 'The Craig Newmark Graduate School of Journalism combines mission-driven reporting, practical skills and an inclusive newsroom culture for the next generation of journalists.';

  // Related stories
  const relatedStories = [
    { headline: 'How America\'s top news organizations escape rigid publishing systems to design beautiful data-driven stories on deadline.', href: 'https://palewi.re/docs/coding-the-news/' },
    { headline: 'How to install, configure and use Visual Studio Code, GitHub and Copilot', href: 'https://palewi.re/docs/coding-the-news/scripts/week-1/' },
    { headline: "How to publish a website with Node.JS and GitHub Actions", href:"https://palewi.re/docs/coding-the-news/scripts/week-2/"},
  ];

  const emmaHeaderLinks = [
    { label: 'Admissions', href: 'https://www.journalism.cuny.edu/admissions/' },
    { label: 'Programs', href: 'https://www.journalism.cuny.edu/academics/' },
    { label: 'Apply', href: 'https://www.journalism.cuny.edu/admissions/how-to-apply/' },
  ];
</script>

<!-- This sets the page title in the browser tab -->
<svelte:head>
  <title>{headline} | NYCity News Service</title>
  <meta name="description" content="At the Craig Newmark Graduate School of Journalism at the City University of New York, change is in our DNA. That comes of being born in 2006, as the digital revolution was transforming our profession in ways none of us could have imagined." />
</svelte:head>

<!-- Your page content goes here -->
<article class="cuny-story">
  <header class="emma-site-header" aria-label="Site header">
    <div class="emma-site-header-inner">
      <span class="emma-site-brand">EMMA News Service</span>
      <nav aria-label="EMMA News Service links" class="emma-site-nav">
        <ul class="emma-site-nav-list">
          {#each emmaHeaderLinks as link (link.href)}
            <li>
              <a class="emma-site-nav-link" href={link.href}>{link.label}</a>
            </li>
          {/each}
        </ul>
      </nav>
    </div>
  </header>

  <SplashHeader
    kicker="CUNY IMPACT"
    {headline}
    {dek}
    {byline}
    {pubDate}
    backgroundImage="/example-photo.gif"
    backgroundAlt="Students at the Craig Newmark Graduate School of Journalism"
  />

  <div class="story-shell">
    <Dashboard>
      <BigNumber number="15,000+" label="Alumni Working in Media" footnote="Graduates placed across local, national and global outlets" />
      <BigNumber number="87%" label="Students on Scholarship Aid" footnote="Expanded access through donor-backed support" />
      <BigNumber number="3" label="Innovation Centers" footnote="Research, entrepreneurship and community reporting" />
    </Dashboard>

    <!-- Article Body: The main story text with proper typography -->
    <ArticleBody>
      <p>
        At the Craig Newmark Graduate School of Journalism at the City University of New York, change is in our DNA. That comes of being born in 2006, as the digital revolution was transforming our profession in ways none of us could have imagined.
      </p>

      <p>
        We fashioned a school to teach the latest storytelling, entrepreneurial, and technological skills alongside reporting, writing, and ethics. Beyond that, we’ve crafted a culture that spurns complacency, that isn’t afraid to pivot before the ground under us shifts.
      </p>

      <p>
        Our mission is to serve the public interest – by training new journalists from varied economic, racial, and cultural backgrounds who will bring much-needed diversity to newsrooms, by helping mid-career journalists retool their skills, and by partnering with other media organizations to find new paths to excellence.
      </p>

      <p>
        Our low tuition rates, along with the added backing of private donors, allow candidates for our master’s degrees in journalism and engagement journalism to receive a world-class education at an affordable price. We also offer a unique bilingual master’s in journalism for students fluent in English and Spanish.
      </p>

      <div class="statue-inline">
        <Image
          src="https://upload.wikimedia.org/wikipedia/commons/a/a1/Statue_of_Liberty_7.jpg"
          alt="The Statue of Liberty in New York Harbor"
          caption="The Statue of Liberty stands as a symbol of opportunity and civic ideals in New York City."
          credit="Photo: William Warby / Wikimedia Commons"
          size="medium"
        />
      </div>

      <p>
        Our three media centers provide research, training, thought leadership, industry meet-ups, and financial support for quality journalistic work.
      </p>

      <p>
        We also offer a robust professional education program through regular evening and weekend workshops. And we support in-depth reporting projects of professional journalists through fellowship grants.
      </p>

      <p>
        Classes are led by accomplished full-time faculty and adjuncts, who tap their networks to help students and graduates find internships, freelance opportunities and — the ultimate prize — jobs.
      </p>

      <p>
        At a time when our profession is reeling from financial pressures and lack of trust, the Newmark Graduate School of Journalism is committed to producing the next generation of skilled, ethically minded, and diverse journalists.
      </p>

      <p>
        We invite you to be part of our world.
      </p>
    </ArticleBody>

    <Image
      src="/example-photo.gif"
      alt="The Craig Newmark Graduate School of Journalism is at 219 West 40th Street in Midtown Manhattan."
      caption="The Craig Newmark Graduate School of Journalism is at 219 West 40th Street in Midtown Manhattan."
      credit="Craig Newmark Graduate School of Journalism"
      size="large"
    />

    <!-- Related Stories: Links to other articles -->
    <RelatedLinks
      title="Related Stories"
      links={relatedStories}
    />
  </div>
</article>

<style lang="scss">
  @use '$lib/styles' as *;

  .cuny-story {
    --color-accent: var(--story-cuny-accent);
    --color-dark: var(--story-cuny-ink);
    --color-text: var(--story-cuny-body);
    --color-white: var(--story-cuny-paper);
    --color-light-gray: var(--story-cuny-surface);
    --color-medium-gray: var(--story-cuny-muted);
    --color-border: var(--story-cuny-border);
    --font-serif: var(--font-serif-display);
    --font-sans: var(--font-sans-ui);
    background: var(--story-cuny-page-gradient);
    color: var(--color-text);
    padding-bottom: var(--spacing-xxl);
  }

  .emma-site-header {
    width: var(--size-full);
    background: var(--story-cuny-card-bg);
    border-bottom: var(--border-width-thin) solid var(--story-cuny-border);
    box-shadow: var(--shadow-soft);
  }

  .emma-site-header-inner {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: space-between;
    gap: var(--spacing-sm);
    width: var(--size-full);
    max-width: var(--max-width-wide);
    margin: var(--spacing-none) var(--size-auto);
    padding: var(--spacing-sm) var(--spacing-md);
  }

  .emma-site-brand {
    font-family: var(--font-sans-ui);
    font-size: var(--font-size-xl);
    font-weight: var(--font-weight-bold);
    letter-spacing: var(--letter-spacing-wide);
    text-transform: uppercase;
    color: var(--story-cuny-card-text);
  }

  .emma-site-nav-list {
    list-style: none;
    display: flex;
    flex-wrap: wrap;
    gap: var(--spacing-sm);
    margin: var(--spacing-none);
    padding: var(--spacing-none);
  }

  .emma-site-nav-link {
    font-family: var(--font-sans-ui);
    font-size: var(--font-size-sm);
    font-weight: var(--font-weight-semibold);
    letter-spacing: var(--letter-spacing-wide);
    text-transform: uppercase;
    color: var(--story-cuny-card-text);
    text-decoration: none;
    border-bottom: var(--border-width-thin) solid transparent;
    transition: var(--transition-color);
  }

  .emma-site-nav-link:hover {
    color: var(--story-cuny-highlight);
    border-bottom-color: var(--story-cuny-highlight);
  }

  .story-shell {
    width: var(--size-full);
    max-width: var(--max-width);
    margin: var(--spacing-xl) var(--size-auto) var(--spacing-none);
    padding: var(--spacing-none) var(--spacing-md);
  }

  .story-shell :global(.row) {
    margin-top: var(--spacing-none);
  }

  .story-shell :global(.big-number) {
    background-color: var(--story-cuny-card-bg);
    color: var(--story-cuny-card-text);
    border: var(--border-width-thin) solid var(--story-cuny-border);
    box-shadow: var(--shadow-soft);
  }

  .story-shell :global(.big-number .number) {
    color: var(--story-cuny-card-number);
    font-family: var(--font-serif-display);
  }

  .story-shell :global(.big-number .label),
  .story-shell :global(.big-number .footnote) {
    color: var(--story-cuny-card-text);
    font-family: var(--font-sans-ui);
  }

  .story-shell :global(.article-body) {
    font-family: var(--font-sans-ui);
  }

  .story-shell :global(.article-body::after) {
    content: '';
    display: block;
    clear: both;
  }

  .story-shell :global(.statue-inline) {
    float: left;
    width: var(--max-width-image-medium);
    max-width: var(--size-full);
    margin: var(--spacing-xxs) var(--spacing-md) var(--spacing-sm) var(--spacing-none);
  }

  .story-shell :global(.statue-inline .image-figure) {
    margin: var(--spacing-none);
  }

  .story-shell :global(.statue-inline .size-medium) {
    max-width: var(--size-full);
  }

  @include mobile {
    .story-shell {
      margin-top: var(--spacing-lg);
    }

    .story-shell :global(.statue-inline) {
      float: none;
      width: var(--size-full);
      margin: var(--spacing-md) var(--spacing-none);
    }
  }
</style>
