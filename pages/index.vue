<template>
  <div class="container-fluid px-0">
    <div class="boder" style="max-width:200px; flex:auto;">
      <input v-model="number" type="text" />
    </div>
    <div class="boder" style="max-width:100%; flex:auto;">
      <select v-model="option" name="" id="">
        <option value="prime">isPrime</option>
        <option value="fiba">IsFibanacci</option>
      </select>
    </div>
    <div style="max-width:300px; flex:auto;">{{ cal }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      number: "",
      option: "prime"
    };
  },
  methods: {
    check() {
      if (this.number < 0) this.number = 1;
      if (/[a-zA-Z]/.test(this.number) && this.number.match(/\d+/)) {
        return this.number.match(/\d+/);
      } else {
        return this.number;
      }
    },
    isSquare(n) {
      return n > 0 && Math.sqrt(n) % 1 === 0;
    }
  },
  computed: {
    cal: function() {
      switch (this.option) {
        case "prime":
          let isPrime = true;
          if (this.number == 1) {
            return false;
          } else if (this.check() > 1) {
            // looping through 2 to number-1
            for (let i = 2; i < this.check(); i++) {
              if (this.check() % i == 0) {
                isPrime = false;
                break;
              }
            }
            if (isPrime) {
              return true;
            } else {
              return false;
            }
          }
          break;
        case "fiba":
          if (
            this.isSquare(5 * (this.check() * this.check()) - 4) ||
            this.isSquare(5 * (this.check() * this.check()) + 4)
          ) {
            return true;
          } else {
            return false;
          }
          break;
      }
    }
  }
};
</script>

<style>
.boder {
  border-right: 1px solid #000;
}
.container-fluid {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;

  /* justify-content: center;
  align-items: center;
  text-align: center; */
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
