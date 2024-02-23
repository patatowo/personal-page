<script>
export default {
  name: "typeWiriter",
  data: () => {
    return {
      typeValue: "",
      typeStatus: false,
      displayTextArray: [
        "hobby web developer",
        "software engineering student",
        "hobby graphic designer",
        "hobby game developer",
      ],
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
      if (
        this.charIndex <
        this.displayTextArray[this.displayTextArrayIndex].length
      ) {
        if (!this.typeStatus) this.typeStatus = true;
        this.typeValue += this.displayTextArray[
          this.displayTextArrayIndex
        ].charAt(this.charIndex);
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
        this.typeValue = this.displayTextArray[
          this.displayTextArrayIndex
        ].substring(0, this.charIndex - 1);
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
        <h2>I'm</h2>
        <h2 class="lysia">Silvia</h2>
      </div>
      <div class="container">
        <h2>
          I'm a
          <span class="typed-text">{{ typeValue }}</span>
          <span class="blinking-cursor">|</span>
          <span class="cursor" :class="{ typing: typeStatus }">&nbsp;</span>
        </h2>
      </div>
    </div>
  </main>
</template>

<style lang="scss">
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
    color: var(--special-color);
  }
}

// Cursor blinking CSS Starts...
.blinking-cursor {
  font-size: 1em;
  color: var(--special-color);
  animation: 1s blink step-end infinite;
}

@keyframes blink {
  from,
  to {
    color: transparent;
  }

  50% {
    color: var(--special-color);
  }
}

@-moz-keyframes blink {
  from,
  to {
    color: transparent;
  }

  50% {
    color: var(--special-color);
  }
}

@-webkit-keyframes blink {
  from,
  to {
    color: transparent;
  }

  50% {
    color: var(--special-color);
  }
}

@-ms-keyframes blink {
  from,
  to {
    color: transparent;
  }

  50% {
    color: var(--special-color);
  }
}

@-o-keyframes blink {
  from,
  to {
    color: transparent;
  }

  50% {
    color: var(--special-color);
  }
}

.page--home {
  padding-left: 2em;
  padding-right: 2em;
}

.introduction {
  padding-top: 5em;
  padding-left: 4em;

  h1 {
    font-family: var(--font-family-special);
    font-size: 5em;
    margin-bottom: 0;
  }

  .name {
    display: flex;
    flex-direction: row;
    gap: 1em;

    .lysia {
      color: var(--secondary-color);
    }

    h2 {
      font-family: var(--font-family-special);
      font-size: 4em;
      margin-top: 0;
    }
  }

  .hobby {
    h2 {
      font-family: var(--font-family-special);
      color: var(--special-color);
      font-size: 2em;
      margin-top: 0;
    }
  }
}
</style>

