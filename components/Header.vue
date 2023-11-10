<template>
	<header class="header">
		<p>
			SILVIA GUERRERO
		</p>
		<ul>
			<li>
				<NuxtLink to="/">HOME</NuxtLink>
			</li>

			<li>
				<NuxtLink to="/about">ABOUT</NuxtLink>
			</li>
			<li>
				<NuxtLink to="/projects">PROJECTS</NuxtLink>
			</li>
			<li>
				<NuxtLink to="/contact">CONTACT</NuxtLink>
			</li>
		</ul>
	</header>
</template>

<style lang="scss">
.header {
	display: flex;
	justify-content: space-between;
	padding-left: 2em;
	padding-right: 2em;

	p {
		font-family: var(--font-family-special);
		display: flex;
		justify-content: flex-start;
	}

	ul {
		list-style: none;

		font-family: var(--font-family-special);

		display: flex;
		justify-content: flex-end;
		gap: 1em;



		li {
			a {
				text-decoration: none;
				color: var(--fg-color);
				opacity: 0.75;

				transition: opacity 0.25s ease-out;

				&:hover {
					opacity: 1;
				}

				// COPY PASTE https://www.30secondsofcode.org/css/s/hover-underline-animation/
				display: inline-block;
				position: relative;

				&::after {
					content: '';
					position: absolute;
					width: 100%;
					transform: scaleX(0);
					height: 2px;
					bottom: 0;
					left: 0;
					background-color: #aaa574;
					transform-origin: bottom right;
					transition: transform 0.25s ease-out;
				}

				&:hover::after {
					transform: scaleX(1);
					transform-origin: bottom left;
				}

				// END COPY PASTE
			}

		}
	}
}
</style>