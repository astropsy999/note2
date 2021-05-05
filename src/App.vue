<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <h1>{{ title }}</h1>
          <message v-if="message" :message="message"></message>

          <div class="new-note">
            <input v-model="note.title" type="text" />
            <textarea v-model="note.descr"></textarea>
            <button @click="addNote">New Note</button>
          </div>
          <div class="notes">
            <div class="note" v-for="(note, index) in notes" :key="index">
              <div class="note-header">
                <p>{{ note.title }}</p>
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
import Message from '@/components/Message.vue'
export default {
  data() {
    return {
      title: 'Notes App',
      message: 'Component Message',
      note: {
        title: '',
        descr: '',
      },
      notes: {
        title: 'First Note',
        descr: '',
        data: new Date().toLocaleString(),
      },
    }
  },
  components: {
    Message,
  },
}
</script>

<style>
.wrapper {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
    Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  margin: 5px auto;
  padding: 10px;
  width: 40%;
  border: 1px solid lightgrey;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
}
.new-note {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  width: 100%;
}
.new-note input {
  width: 80%;
  margin: 5px;
  border-radius: 10px;
  outline: none;
}
.new-note textarea {
  width: 80%;
  margin: 5px;
  border-radius: 10px;
  outline: none;
}
.new-note button {
  padding: 10px 20px;
  border-radius: 10px;
  outline: none;
}
</style>
