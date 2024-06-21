<script>
export default {
  data() {
    return {
      showModal: false,
      newNote: "",
      errorMessage: "",
      notes: [],
    };
  },
  methods: {
    getRandomColor() {
      return "hsl(" + Math.random() * 360 + ", 100%, 75%)";
    },
    addNote() {
      this.errorMessage = "";
      if (this.newNote.trim.length < 10) {
        return (this.errorMessage = "Note nedds to be 10 character or more");
      }
      this.notes.push({
        id: Math.floor(Math.random() * 1000000),
        text: this.newNote,
        date: new Date(),
        backGroundColor: this.getRandomColor(),
      });
      this.showModal = false;
      this.newNote = "";
    },
  },
};
</script>

<template>
  <main>
    <div class="overlay" v-if="showModal">
      <div class="modal">
        <textarea
          v-model="newNote"
          name="note"
          id="note"
          cols="30"
          rows="10"
        ></textarea>
        <p v-if="errorMessage">{{ errorMessage }}</p>
        <button @click="addNote">Add Note</button>
        <button class="close" @click="this.showModal = false">Close</button>
      </div>
    </div>
    <div class="container">
      <header>
        <h1>Notes</h1>
        <button @click="this.showModal = true">+</button>
      </header>
      <div class="cards-container">
        <div
          v-for="(note, index) in notes"
          :key="index"
          class="card"
          :style="{ backgroundColor: note.backGroundColor }"
        >
          <div class="main-text">
            {{ note.text }}
          </div>
          <div class="date">{{ note.date.toLocaleDateString("en-US") }}</div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  height: 100vh;
  width: 100vw;
}

.container {
  max-width: 1000px;
  padding: 10px;
  margin: 0 auto;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h1 {
  font-weight: bold;
  margin-bottom: 25px;
  font-size: 75px;
}

button {
  border: none;
  padding: 10px;
  width: 50px;
  height: 50px;
  cursor: pointer;
  background-color: rgb(21, 20, 21);
  border-radius: 100%;
  color: white;
  font-size: 20px;
}

.cards-container {
  display: flex;
  flex-wrap: wrap;
}

.card {
  width: 225px;
  height: 225px;
  background-color: rgb(237, 182, 44);
  padding: 10px;
  border-radius: 15px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-right: 20px;
  margin-bottom: 20px;
}

.date {
  font-size: 12.5px;
  font-weight: bold;
}

.overlay {
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: rgb(0, 0, 0, 0.77);
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal {
  width: 750px;
  background-color: white;
  border-radius: 10px;
  padding: 30px;
  position: relative;
  display: flex;
  flex-direction: column;
}

.modal button {
  padding: 10px 20px;
  font-size: 20px;
  width: 100%;
  background: blueviolet;
  border: none;
  color: white;
  margin-top: 15px;
  border-radius: 0;
}

.modal .close {
  background-color: rgb(193, 15, 15);
}

.modal p {
  margin-bottom: 0;
  color: red;
}
</style>
