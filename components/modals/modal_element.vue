<template>
  <div class="content_model">
    <div class="model_chosed" @click="closedModal">
      <span />
      <span />
    </div>
    <p>CLOSED</p>
    <div class="content_data_element">
      <cell :object-element="dataElement" />
      <div class="content_data_element--text">
        <!-- <p>{{ dataElement }}</p> -->
        <p>{{ dataElement.symbol }}</p>
        <p>{{ dataElement.atomicMass}}</p>
        <p>{{ dataElement.electronicConfiguration}}</p>
        <p>{{ dataElement.electronegativity}}</p>
        <p>{{ dataElement.atomicRadius}}</p>
        <p>{{ dataElement.ionRadius}}</p>
        <p>{{ dataElement.bondingType}}</p>
      </div>
    </div>
  </div>
</template>

<script>
import cell from '~/components/cells/cell.vue'
export default {
  components: {
    cell
  },
  props: {
    dataElement: {
      type: Object,
      default: () => {}
    }
  },
  methods: {
    closedModal() {
      this.$emit('closedModal')
    }
  }
}
</script>

<style scoped>

.content_model {
  z-index: 100;
  color: white;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.model_chosed {
  border-radius: 45px;
  position: relative;
  width: 45px;
  height: 45px;
  margin: 1rem;
  cursor: pointer;
}

.model_chosed > span {
  position: absolute;
  top: calc(50% - 20px);
  left: calc(50%);
  border: 2px solid white;
  min-height: 40px;
  transition: 1.5s;
}

.content_data_element {
  align-items: center;
  border: 1px solid white;
  display: flex;
  margin-top: 3rem;
  margin: 5rem;
  padding: 2rem;
  /* animation: openModal 3s; */
}

@keyframes openModal {
  0%   {
    border: 0;
  }
  25%  {
    border-bottom: 1px solid white;
  }
  50%  {
    border-left: 1px solid white;
  }
  75%  {
    border-top: 1px solid white;
  }
  100% {
    border-left: 1px solid white;
  }
}

.content_data_element--text {
  min-width: 800px;
}

.content_data_element > div {
  margin: 0 1rem;
}

.model_chosed > span:nth-of-type(1) {
  transform: rotate(45deg);
}

.model_chosed > span:nth-of-type(2) {
  transform: rotate(-45deg);
}

.model_chosed:hover > span:nth-of-type(1) {
  transform: rotate(765deg);
}

.model_chosed:hover > span:nth-of-type(2) {
  transform: rotate(-765deg);
}
</style>
