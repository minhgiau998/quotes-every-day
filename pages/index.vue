<template>
  <div class="container">
    <div class="title has-text-centered">
      <p v-if="$fetchState.pending">
        <img src="../assets/svg/loading.svg" />
      </p>
      <p v-else-if="$fetchState.error">
        Error while fetching posts: {{ $fetchState.error.message }}
      </p>
      <div v-else>
        <h1 class="quotes">
          {{ quotes.data.content }}
        </h1>
        <p class="author">
          {{ quotes.data.author }}
        </p>
        <b-taglist class="tag-list">
          <b-tag
            class="tag-list__item"
            v-for="(tag, index) in quotes.data.tags"
            :key="index"
          >
            {{ tag }}
          </b-tag>
        </b-taglist>
      </div>
      <b-button type="is-warning" size="is-large" @click="refresh">
        <p>Roll</p>
      </b-button>
    </div>
  </div>
</template>

<script>
export default {
  layout: "home",
  data() {
    return {
      quotes: null
    };
  },
  async fetch() {
    this.quotes = await this.$axios.get("https://api.quotable.io/random");
  },
  mounted() {
    this.$nextTick(() => {
      this.$nuxt.$loading.start();
      this.$fetch();
      this.$nuxt.$loading.finish();
    });
  },
  methods: {
    refresh() {
      this.$nuxt.$loading.start();
      this.$fetch();
      this.$nuxt.$loading.finish();
    }
  }
};
</script>

<style lang="scss">
.theme-dark {
  background-color: $mineShaft;
  color: $kournikova;

  .title {
    color: $mineShaft;
  }

  .quotes {
    color: $white;
  }

  .author {
    color: $white;
    opacity: 0.5;
  }

  .tag:not(body) {
    color: $mineShaft;
    background-color: $wildSand;
  }
}

::-webkit-scrollbar {
  width: 0px;
}

.quotes {
  font-family: "BureauGrotesque-OneSeven", Impact, sans-serif;
  text-transform: uppercase;
  font-size: 50px;
  color: $mineShaft;
  -webkit-font-smoothing: antialiased;
  margin-bottom: 10px;

  &::before {
    content: "\201C";
  }

  &::after {
    content: "\201D";
  }
}

.author {
  font-size: 25px;
  color: $mineShaft;
  opacity: 0.5;
  font-family: courier, mono-space;
}

.tag-list {
  justify-content: center;
  padding: 20px 0px;
}

.tag:not(body) {
  color: $wildSand;
  background-color: $mineShaft;
}
</style>
