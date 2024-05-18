<template>
  <div class="child-container">
    <h2>Child Component</h2>
    <p>
      Data from Grandchild: <span class="data">{{ dataFromGrandchild }}</span>
    </p>
    <GrandChildComponent @grandChildData="handleGrandChildData" />
    <slot :message="slotMessage"></slot>
  </div>
</template>

<script>
import GrandChildComponent from "./GrandChildComponent.vue";

export default {
  components: {
    GrandChildComponent,
  },
  data() {
    return {
      dataFromGrandchild: null,
      slotMessage: "Hello from Child Component!",
    };
  },
  methods: {
    handleGrandChildData(data) {
      this.dataFromGrandchild = data;
      this.$emit("childData", data);
    },
  },
};
</script>

<style scoped>
.child-container {
  padding: 20px;
  border: 2px solid #2196f3;
  border-radius: 10px;
  background-color: #f1f8e9;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
  margin-top: 20px;
  text-align: center;
  transition: transform 0.3s;
}
.child-container:hover {
  transform: scale(1.02);
}
.data {
  color: #ff9800;
  font-weight: bold;
  animation: bounce 1.5s infinite;
}
@keyframes bounce {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}
h2 {
  color: #2e7d32;
}
p {
  font-size: 18px;
  font-family: "Arial", sans-serif;
}
</style>
