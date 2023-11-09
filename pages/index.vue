<script>
export default {
	name: "typeWiriter",
	data: () => {
		return {
			typeValue: "",
			typeStatus: false,
			displayTextArray: ["web developer", "graphic designer", "game developer"],
			typingSpeed: 100,
			erasingSpeed: 100,
			newTextDelay: 2000,
			displayTextArrayIndex: 0,
			charIndex: 0,
		};
	},
	props: {},
	created() {
		setTimeout(this.typeText, this.newTextDelay + 200);
	},
	methods: {
		typeText() {
			if (this.charIndex < this.displayTextArray[this.displayTextArrayIndex].length) {
				if (!this.typeStatus) this.typeStatus = true;
				this.typeValue += this.displayTextArray[this.displayTextArrayIndex].charAt(
					this.charIndex
				);
				this.charIndex += 1;
				setTimeout(this.typeText, this.typingSpeed);
			} else {
				this.typeStatus = false;
				setTimeout(this.eraseText, this.newTextDelay);
			}
		},
		eraseText() {
			if (this.charIndex > 0) {
				if (!this.typeStatus) this.typeStatus = true;
				this.typeValue = this.displayTextArray[this.displayTextArrayIndex].substring(
					0,
					this.charIndex - 1
				);
				this.charIndex -= 1;
				setTimeout(this.eraseText, this.erasingSpeed);
			} else {
				this.typeStatus = false;
				this.displayTextArrayIndex += 1;
				if (this.displayTextArrayIndex >= this.displayTextArray.length)
					this.displayTextArrayIndex = 0;
				setTimeout(this.typeText, this.typingSpeed + 1000);
			}
		},
	},
};
</script>

<template>
	<main class="page page--home">
		<div class="introduction">
			<h1>Hi there!</h1>
			<div class="name">
				<h2>I'm </h2>
				<h2 class="lysia"> Lysia</h2>
			</div>
			<div class="container">
				<h2>
					I'm a hobby
					<span class="typed-text">{{ typeValue }}</span>
					<span class="blinking-cursor">|</span>
					<span class="cursor" :class="{ typing: typeStatus }">&nbsp;</span>
				</h2>
			</div>
		</div>
	</main>
</template>

<style lang="scss" scoped>
.container {
	display: flex;
	justify-content: left;
	align-items: center;
	margin-top: 0;
	height: 1em;
}

h2 {
	font-size: 3em;
	font-weight: normal;

	span.typed-text {
		color: #757147;
	}
}

// Cursor blinking CSS Starts...
.blinking-cursor {
	font-size: 1em;
	color: #757147;
	-webkit-animation: 1s blink step-end infinite;
	-moz-animation: 1s blink step-end infinite;
	-ms-animation: 1s blink step-end infinite;
	-o-animation: 1s blink step-end infinite;
	animation: 1s blink step-end infinite;
}

@keyframes blink {

	from,
	to {
		color: transparent;
	}

	50% {
		color: #757147;
	}
}

@-moz-keyframes blink {

	from,
	to {
		color: transparent;
	}

	50% {
		color: #757147;
	}
}

@-webkit-keyframes blink {

	from,
	to {
		color: transparent;
	}

	50% {
		color: #757147;
	}
}

@-ms-keyframes blink {

	from,
	to {
		color: transparent;
	}

	50% {
		color: #757147;
	}
}

@-o-keyframes blink {

	from,
	to {
		color: transparent;
	}

	50% {
		color: #757147;
	}
}

.page--home {
	padding-left: 2em;
	padding-right: 2em;
	background-color: var(--primary-color);
}

.introduction {
	padding-top: 5em;
	padding-left: 4em;


	h1 {
		font-family: var(--font-family-special);
		color: var(--primary-color);
		font-size: 5em;
		margin-bottom: 0;
		font-weight: normal;
	}



	.name {
		display: flex;
		flex-direction: row;
		gap: 1em;

		.lysia {
			color: #757147;
		}

		h2 {
			font-family: var(--font-family-special);
			color: var(--primary-color);
			font-size: 4em;
			margin-top: 0;
		}
	}

	.hobby {

		h2 {
			font-family: var(--font-family-special);
			color: var(--primary-color);
			font-size: 3em;
			margin-top: 0;
		}
	}

}
</style>