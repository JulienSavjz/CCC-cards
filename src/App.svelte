<script>
  import { onMount } from "svelte";

	import Search from "./Search.svelte";
	import CardList from "./Cards.svelte";
	import Card from "./lib/components/CardProxy.svelte";

	let showcase, vintage, original, bookCover, prototype;

	let query = "";
	let isLoading = true;

	const getCards = async () => {
		let cardFetch = await fetch("/data/cards.json");
		let cards = await cardFetch.json();
		return cards;
	};

	const loadCards = async() => {
		return getCards()
			.then((cards) => {
				window.cards = cards;
				showcase = cards.find((card) => card.id === "EmuNl");
				vintage = cards.filter((card) => card.category === "vintage");
				original = cards.filter((card) => card.category === "original");
				bookCover = cards.filter((card) => card.category === "book-cover");
				prototype = cards.filter((card) => card.category === "prototype");
				isLoading = false;
			});
	};

	onMount(() => {
		loadCards();
		const $headings = document.querySelectorAll("h1,h2,h3");
		const $anchor = [...$headings].filter((el) => {
			const id = el.getAttribute("id")?.replace(/^.*?-/g,"");
			const hash = window.location.hash?.replace(/^.*?-/g,"")
			return id === hash;
		})[0];
		if( $anchor ) {
			setTimeout(() => {
				$anchor.scrollIntoView();
			},100);
		}
	});
</script>

<main>
	<header>
		<h1 id="⚓-top">Chroma Custom Cards</h1>

		<p class="author">By <a href="https://www.instagram.com/chroma.custom.cards/">Chroma Custom Cards</a></p>

		
		
		<section class="intro" id="⚓-intro">
			<p>
				<mark>Custom</mark> <mark>Magic: The Gathering</mark> cards, forged in
				the blackest depths. Move your cursor over a card to tilt it in
				<mark>3D</mark> and take a closer look at every <mark>illustration</mark>.
			</p>
			<p>
				Illustrator and graphic designer, I’m passionate about
				<mark>Lands</mark>, the color <mark>black</mark> and, right after it,
				<mark>blue</mark>, but I have a huge soft spot for
				<mark>artifacts</mark>.I create memorable cards for cards lover and for collection.
			</p>
			<p>
				Every original illustration is <mark>custom-made</mark>. Some
				illustrations come from the public domain, but they require an
				enormous amount of restoration work before they’re ready to print.
			</p>
			<p>
				Every card follows the original standard: weight, density, quality and
				materials, <mark>black core</mark> included.
			</p>
		</section>
		
		
		
		
		
		
		

		<div class="showcase">
			{#if !showcase}
				loading...
			{:else}
				<Card
					id={showcase.id}
					name={showcase.name}
					img={showcase.img}
					showcase={true}
				/>
			{/if}
		</div>

		<section class="info">
			<h2>Click on a Card to take a Closer look!</h2>

			<hr />

			
		</section>
	</header>

	<Search bind:query />

	{#if query.length < 3}

		<h2 id="⚓-vintage">
			<a href="#⚓-vintage">
				Vintage Framed
			</a>
		</h2>
		<p>
			Cards inspired by the <mark>earliest printings</mark> of the game, with the
			<mark>classic frames and old-school look</mark> of the original sets especialy the seven edition.
		</p>

		<CardList>
			{#if isLoading}
				loading...
			{:else}
				{#each vintage as card, index}
					<Card
						id={card.id}
						name={card.name}
						img={card.img}
					/>
				{/each}
			{/if}
		</CardList>

		<h2 id="⚓-original">
			<a href="#⚓-original">
				Original Artwork
			</a>
		</h2>
		<p>
			The <mark>core of the collection</mark>: custom versions of iconic cards, 
			redrawn with a <mark>fresh frame and illustration</mark>.
		</p>

		<CardList>
			{#if isLoading}
				loading...
			{:else}
				{#each original as card, index}
					<Card
						id={card.id}
						name={card.name}
						img={card.img}
					/>
				{/each}
			{/if}
		</CardList>

		<h2 id="⚓-book-cover">
			<a href="#⚓-book-cover">
				Book Cover
			</a>
		</h2>
		<p>
			Cards designed like the <mark>cover of a book</mark>, where the artwork
			takes the spotlight and the frame becomes part of the <mark>illustration</mark>.
		</p>

		<CardList>
			{#if isLoading}
				loading...
			{:else}
				{#each bookCover as card, index}
					<Card
						id={card.id}
						name={card.name}
						img={card.img}
					/>
				{/each}
			{/if}
		</CardList>

		<h2 id="⚓-Japanese">
			<a href="#⚓-Japanese">
				Japanese Version
			</a>
		</h2>
		<p>
			<mark>Japanese Land cards </mark>: alternate versions, 
			own work and other ideas from domain public.
		</p>

		<CardList>
			{#if isLoading}
				loading...
			{:else}
				{#each prototype as card, index}
					<Card
						id={card.id}
						name={card.name}
						img={card.img}
					/>
				{/each}
			{/if}
		</CardList>
		
		<h2 id="⚓-Prototype">
			<a href="#⚓-Prototype">
				Prototype Version
			</a>
		</h2>
		<p>
			<mark>Prototype version similar to zeta set </mark>: alternate versions, 
			own work and other ideas from domain public.
		</p>

		<CardList>
			{#if isLoading}
				loading...
			{:else}
				{#each prototype as card, index}
					<Card
						id={card.id}
						name={card.name}
						img={card.img}
					/>
				{/each}
			{/if}
		</CardList>
		
		<h2 id="⚓-Land">
			<a href="#⚓-Land">
				Land
			</a>
		</h2>
		<p>
			<mark>All land cards</mark>: alternate versions, 
			own work and other ideas that may become part of the collection later.
		</p>

		<CardList>
			{#if isLoading}
				loading...
			{:else}
				{#each prototype as card, index}
					<Card
						id={card.id}
						name={card.name}
						img={card.img}
					/>
				{/each}
			{/if}
		</CardList>
		
		<h2 id="⚓-Other-Licences-Pokemon">
			<a href="#⚓-Other-Licences-Pokemon">
				Other Licences
			</a>
		</h2>
		<p>
			<mark>Pokemon:</mark>  
			From traditional black and white to rich color.
		</p>

		<CardList>
			{#if isLoading}
				loading...
			{:else}
				{#each prototype as card, index}
					<Card
						id={card.id}
						name={card.name}
						img={card.img}
					/>
				{/each}
			{/if}
		</CardList>
		
		<h2 id="⚓-Other-Licences-Berserk">
			<a href="#⚓-Other-Licences-Berserk">
				Other Licences
			</a>
		</h2>
		<p>
			<mark>Berserk:</mark>:  
			own work and remaster of existing artwork (berserk especialy).
		</p>

		<CardList>
			{#if isLoading}
				loading...
			{:else}
				{#each prototype as card, index}
					<Card
						id={card.id}
						name={card.name}
						img={card.img}
					/>
				{/each}
			{/if}
		</CardList>

	{/if}
</main>

<div class="back-to-top">
  <a href="#⚓-top">Back to Top</a>
</div>

<style>
  .back-to-top a {
    color: inherit;
    text-decoration: none;
		z-index: 999;
  }
</style>
