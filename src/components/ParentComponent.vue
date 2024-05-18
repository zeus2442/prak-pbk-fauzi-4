<template>
  <div class="parent-container">
    <h1>Parent Component</h1>
    <p>
      Data from Child: <span class="data">{{ dataFromChild }}</span>
    </p>
    <ChildComponent @childData="handleChildData">
      <template v-slot:default="{ message }">
        <div class="slot-content">
          <h2>Message from Slot:</h2>
          <p>{{ message }}</p>
        </div>
      </template>
    </ChildComponent>
  </div>
</template>

<script>
import ChildComponent from "./ChildComponent.vue";

export default {
  components: {
    ChildComponent,
  },
  data() {
    return {
      dataFromChild: null,
    };
  },
  methods: {
    handleChildData(data) {
      this.dataFromChild = data;
    },
  },
};
</script>

<style scoped>
.parent-container {
  padding: 20px;
  border: 2px solid #4caf50;
  border-radius: 10px;
  background-color: #e0f7fa;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
  text-align: center;
  transition: transform 0.3s;
}
.parent-container:hover {
  transform: scale(1.02);
}
.data {
  color: #ff5722;
  font-weight: bold;
  animation: highlight 1.5s infinite;
}
@keyframes highlight {
  0% {
    color: #ff5722;
  }
  50% {
    color: #ffccbc;
  }
  100% {
    color: #ff5722;
  }
}
.slot-content {
  margin-top: 20px;
  padding: 15px;
  border: 1px dashed #2196f3;
  border-radius: 10px;
  background-color: #e3f2fd;
  animation: fadeIn 1s;
}
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
h1,
h2 {
  color: #2c3e50;
}
p {
  font-size: 18px;
  font-family: "Arial", sans-serif;
}
</style>
