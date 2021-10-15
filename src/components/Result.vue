<template>
  <div class="backdrop" @click.self="closeModal" v-if="showPopup">
    <div class="modal" :class="{ sale: theme === 'sales' }">
      <slot>
        <h3 v-if="score">Results are in!</h3>
        <p>{{ rank }}</p>
      </slot>
      <div class="actions">
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["theme", "score"],
  data() {
    return {
      showPopup: true,
      rank: null,
    };
  },
  methods: {
    closeModal() {
      this.showPopup = false;
    },
  },
  mounted() {
    // var scre = this.$props.score;
    var scre = this.score;
    if (scre <= 400) {
      this.rank =
        "Congratulations, You are passed to the next level with best skills";
    } else if (scre > 400 && scre <= 700) {
      this.rank =
        "That was close, You are passed but you will not make it alive in next round";
    } else if (scre > 700 && scre <= 1250) {
      this.rank =
        "Youuu Dead boy";
    } else{
         this.rank =
        "Noob! Get out, You piece of s***!";
    }
  },
};
</script>

<style>
.modal {
  width: 400px;
  padding: 20px;
  margin: 200px auto;
  background: white;
  border-radius: 10px;
}
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}
.modal h1 {
  color: #03cfb4;
  border: none;
  padding: 0;
}
.modal p {
  font-style: normal;
}
.modal .actions {
  text-align: center;
  margin: 30px 0 10px 0;
  color: #333;
}
.modal .actions a {
  color: #333;
  padding: 8px;
  border: 1px solid #eee;
  border-radius: 4px;
  text-decoration: none;
  margin: 10px;
}
/* sale styles */
.modal.sale {
  background: crimson;
  color: white;
}
.modal.sale h1 {
  color: white;
}
.modal.sale .actions {
  color: white;
}
.modal.sale .actions a {
  color: white;
}
</style>
