<template>
  <label class="switch">
    <input type="checkbox" v-on="listeners" />
    <span class="slider round"></span>
  </label>
</template>

<script>
export default {
  computed: {
    listeners() {
      let vm = this;
      return Object.assign({}, this.$listeners, {
        input: function(event) {
          vm.$emit("checked", event.target.checked);
        }
      });
    }
  }
};
</script>

<style>
.switch {
  position: relative;
  margin-top: 13px;
  width: 60px;
  height: 34px;
}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.slider:before {
  position: absolute;
  content: "";
  height: 26px;
  width: 26px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

input:checked + .slider {
  background: linear-gradient(to right, hsl(236, 72%, 79%), hsl(237, 63%, 64%));
}

input:checked + .slider:before {
  -webkit-transform: translateX(26px);
  -ms-transform: translateX(26px);
  transform: translateX(26px);
}

/* Rounded sliders */
.slider.round {
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}
</style>