<template>
	<main class="page page--about">
		<div class="idk">
			<div class="about-me">
				<h1>Know who I am</h1>
				<P>I'm Silvia from Spain. I'm a first year software engineering student
					at the UCLM and I'm a hobby web developer, graphic designer and indie
					game developer on my free time.
				</P>
			</div>
			<img src="\images\Cup-o-coffee-simple.svg.png" />
		</div>

	</main>
</template>

<style lang="scss">
.page--about {

	.idk {
		display: flex;
		gap: 9em;
		margin-top: 5em;
		margin-left: 1em;
		margin-right: 1em;
		padding-top: 1em;
		background-color: var(--primary-color);
		border-radius: 1em;

		.about-me {
			max-width: 29em;
			text-align: justify;
			padding-left: 3em;
			padding-bottom: 5em;

			h1 {
				font-size: 4em;
				font-family: var(--font-family-special);
			}

			p {
				font-size: 1.5em;
			}
		}

		img {
			width: 30em;
			height: 30em;
		}
	}
}
</style>

