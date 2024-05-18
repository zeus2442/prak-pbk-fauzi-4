<template>
  <div class="grandchild-container">
    <h3>Grandchild Component</h3>
    <input v-model="inputData" placeholder="Enter data to send" />
    <button @click="sendData" class="send-button">Send Data to Parent</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputData: "",
    };
  },
  methods: {
    sendData() {
      if (this.inputData.trim()) {
        this.$emit("grandChildData", this.inputData);
        this.inputData = ""; // Clear input after sending
      } else {
        alert("Please enter some data.");
      }
    },
  },
};
</script>

<style scoped>
.grandchild-container {
  padding: 20px;
  border: 2px solid #ff9800;
  border-radius: 10px;
  background-color: #fff3e0;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
  margin-top: 20px;
  text-align: center;
  transition: transform 0.3s;
}
.grandchild-container:hover {
  transform: scale(1.02);
}
input {
  padding: 10px;
  margin-bottom: 10px;
  border: 2px solid #ccc;
  border-radius: 5px;
  width: 80%;
  font-size: 16px;
  box-sizing: border-box;
}
.send-button {
  padding: 10px 20px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
  transition: background-color 0.3s;
}
.send-button:hover {
  background-color: #388e3c;
}
h3 {
  color: #d32f2f;
  font-family: "Comic Sans MS", cursive, sans-serif;
}
</style>
