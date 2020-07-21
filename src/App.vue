<template>
  <div id="app">
    <div class="form col-md-5 m-auto">
      <h3 class="text-center p-3">
        {{ title }}
      </h3>
      <div class="form-group ">
        <input
          class="form-control"
          type="text"
          v-model="note.title"
          placeholder="Enter your memo title!"
        />
      </div>
      <div class="form-group">
        <textarea
          class="form-control"
          v-model="note.text"
          placeholder="Enter your memo text"
        ></textarea>
      </div>
      <button class="btn btn-primary mb-2 btn-lg col-md-12" @click="addNote">
        Post
      </button>
    </div>

    <div class=" row col-md-8 col-lg-12">
      <div class="col-sm-4 mt-4" note v-for="(note, index) in notes">
        <div class="card">
          <button class="close mt-2" @click="deleteNote(index)">
            <i class="fas fa-thumbtack"></i>
          </button>
          <div class="card-block">
            <div class="card-subtitle mb-2 mt-2 text-muted">
              {{ note.date }}
            </div>
            <div class="card-title m-2">{{ note.title }}</div>
            <div class="card-text mb-3">{{ note.text }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      title: "MEMOS",
      note: {
        title: "",
        text: ""
      },
      notes: [
        {
          title: "Try this page 🖐",
          text: "Delete me and create new ones!",
          date: new Date(Date.now()).toLocaleString()
        }
      ]
    };
  },
  methods: {
    addNote: function() {
      let { text, title } = this.note;
      this.notes.push({
        text,
        title,
        date: new Date(Date.now()).toLocaleString()
      });
    },
    deleteNote: function(index) {
      this.notes.splice(index, 1);
    }
  }
};
</script>

<style>
body {
  background: url("https://previews.123rf.com/images/leungchopan/leungchopan1506/leungchopan150600626/41731819-cork-board-background.jpg");
}

h3 {
  font-family: "Roboto Mono", monospace;
}

.form {
  text-align: left;
  background: white;
  border-radius: 2%;
}

.card {
  text-align: center;
  border: none;
  box-shadow: 5px 3px 3px #4a4949;
  background-color: #fc9fbd;
  color: #141414;
  font-family: "Palanquin", sans-serif;
}

.card-title {
  text-transform: uppercase;
  font-weight: bold;
}

.note {
  padding: 5px;
}
</style>
