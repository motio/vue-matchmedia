<style module lang="postcss">
@value breakpoint: (max-width: 600px);

.hello {
  background: #ccc;
}

@media breakpoint {
  .hello {
    background: #f00;
  }
}
</style>

<template>
  <div :class="$style.hello">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      msg: '',
    };
  },
  mounted() {
    this.$nextTick(() => {
      const mql = window.matchMedia(this.$style.breakpoint);
      this.func(mql);
      mql.addListener(this.func);
    });
  },
  methods: {
    func(mql) {
      if (mql.matches) {
        this.msg = 'ウィンドウが 600px 以下です';
      } else {
        this.msg = 'ウィンドウが 601px 以上です';
      }
    },
  },
}
</script>
