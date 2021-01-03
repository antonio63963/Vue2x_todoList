<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <h1>{{ title }}</h1>

          <message v-if="message" :message="message" />
          <!-- <div class="message" v-if="message">
            <p>{{ message }}</p>
          </div> -->
          <!-- new note -->
         <new-note :note="note" @addNote="addNote"/>
          <!-- note list -->
          <div class="notes">
            <div class="note" v-for="(note, index) in notes" :key="index">
              <div class="note-header">
                <h3>{{ note.title }}</h3>
              </div>
              <div class="note-body">
                <p>{{ note.descr }}</p>
                <span>{{ note.date }}</span>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import Message from "./components/Message.vue";
import newNote from "@/components/NewNote.vue";
import NewNote from './components/NewNote.vue';
export default {
  components: {
    Message,
    newNote,
    NewNote,
  },

  data() {
    return {
      title: "Notes App",
      message: null,
      note: {
        title: "",
        descr: "",
      },
      notes: [
        {
          title: "First Note",
          descr: "Description for first note",
          date: new Date(Date.now()).toLocaleDateString(),
        },
        {
          title: "Second Note",
          descr: "Description for Second note",
          date: new Date(Date.now()).toLocaleDateString(),
        },
        {
          title: "Third Note",
          descr: "Description for Third note",
          date: new Date(Date.now()).toLocaleDateString(),
        },
      ],
    };
  },
  methods: {
    addNote() {
      const { title, descr } = this.note;
      if (title === "") {
        this.message = `Title can't be blank`;
        return false;
      }
      this.notes.push({
        title,
        descr,
        date: new Date(Date.now()).toLocaleDateString(),
      });
      this.note.title = "";
      this.note.descr = "";
      this.message = null;
    },
  },
};
</script>

<style>
</style>
