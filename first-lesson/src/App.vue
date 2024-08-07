<template>
  <div class="pet-container">
    <h3>{{ petName ? petName : 'Your Pet' }}</h3>
    <p>Happiness: {{ happiness }}</p>
    <p>{{ message }}</p>

    <input v-model="petName" placeholder="Enter pet name" />
    <button @click="feedPet">Feed Pet</button>
    <button @click="resetHappiness">Reset Happiness</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      petName: '',
      happiness: 0,
      message: 'Your pet is waiting for some love!',
    };
  },
  methods: {
    feedPet() {
        if (this.petName === '') {
           this.updateMessage('Give a name for your sweaty pet')
           return
        }

        if (this.happiness > 90) {
            this.updateMessage('Your pet on the seventh heaven')
            return 
        }
        this.happiness += 10;
        this.updateMessage();
    },
    resetHappiness() {
      this.happiness = 0;
      this.updateMessage();
    },
    updateMessage(msg = null) {
        if (msg !== null) {
            this.message = msg;
            return
        }
      if (this.happiness >= 50) {
        this.message = 'Your pet is very happy!';
      } else if (this.happiness >= 20) {
        this.message = 'Your pet is happy!';
      } else {
        this.message = 'Your pet is waiting for some love!';
      }
    },
  },
};
</script>

<style scoped>

.pet-container {
  max-width: 300px;
  margin: auto;
  text-align: center;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h3 {
  color: #333;
}

p {
  color: #666;
}

input {
  padding: 10px;
  margin: 10px 0;
  border: 1px solid #ccc;
  border-radius: 5px;
  width: calc(100% - 22px);
}

button {
  padding: 10px 20px;
  margin: 5px;
  border: none;
  border-radius: 5px;
  color: white;
  background-color: #28a745;
  cursor: pointer;
}

button:hover {
  background-color: #218838;
}
</style>