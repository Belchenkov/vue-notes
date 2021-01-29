<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <div class="container">
        <h1>{{ title }}</h1>
        <div class="message" v-if="message">
          <p>{{ message }}</p>
        </div>
        <div class="new-note">
          <input v-model="note.title" type="text" />
          <textarea v-model="note.desc"></textarea>
          <button @click="addNote">New Note</button>
        </div>
        <div class="notes">
          <div class="note" v-for="(note, idx) in notes" :key="idx">
            <div class="note-header">
              <p>{{ note.title }}</p>
            </div>
            <div class="note-body">
              <p>{{ note.desc }}</p>
              <span>{{ note.date }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      title: 'Notes Vue',
      note: {
        title: '',
        desc: ''
      },
      message: null,
      notes: [
        {
          title: 'First Note',
          desc: 'Desc for first note',
          date: new Date(Date.now()).toLocaleString()
        },
        {
          title: 'Second Note',
          desc: 'Desc for Second note',
          date: new Date(Date.now()).toLocaleString()
        },
        {
          title: 'Third Note',
          desc: 'Desc for Third note',
          date: new Date(Date.now()).toLocaleString()
        }
      ]
    }
  },
  methods: {
    addNote() {
      if (this.note.title === '') {
        this.message = 'Empty title';
        return false;
      }

      this.notes.push({
        ...this.note,
        date: new Date(Date.now()).toLocaleString()
      });

      this.note = {
        title: '',
        desc: ''
      };

      this.message = null;

    }
  }
}

</script>

<style>

</style>
