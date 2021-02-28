<template>
  <div class="container-fluid p-0 m-0 h-100 text-body">
    <div class="row p-0 m-0 h-100">  
      <div class="col col-4 bg-light p-0 h-100">
        <h3 class="w-100 text-center p-5">
          <i class="bi-pencil-square text-secondary"></i> Elegant Notes
        </h3>
        <button type="button" class="btn btn-dark w-100 py-2 rounded-0" v-on:click="onShowAddForm()">
          <i class="bi-pen-fill text-white"></i> Add note
        </button>
          <notes-list 
            v-bind:notes="notes" 
            v-on:note-remove="onRemoveNote($event)"
            v-on:note-show="onShowNote($event)">
          </notes-list>
      </div>
      <div class="col col-8 bg-white p-0 h-100">
        <div class="cover"></div>
        <div class="p-5">
          <note v-if="currentNote !== null" v-bind:note="currentNote"></note>
          <add-note-form v-else-if="showAddForm" v-on:note-add="onAddNote($event)"></add-note-form>
          <div v-else class="alert alert-secondary" role="alert">
            Nothing to display
          </div>
        </div>
      </div>
    </div>
    <nav class="navbar fixed-bottom navbar-dark bg-dark">
      <div class="container-fluid justify-content-end">
        <span class="text-muted mx-5">©2021 Privacy Policy Terms of Service</span>
        <a class="navbar-brand m-0" href="#"><i class="bi-heart-fill pe-2"></i>My account</a>
      </div>
    </nav>
  </div>
</template>

<script>
  import NotesList from "./components/NotesList.vue";
  import AddNoteForm from "./components/AddNoteForm.vue";
  import Note from "./components/Note.vue";

  export default {
    components: {
      NotesList, 
      AddNoteForm,
      Note
    },
    data: function () {
      return {
        notes: [],
        showAddForm: false,
        currentNote: null,
      }
    },
    methods: {
      onAddNote: function (note){
        var newNote = {
          name: note.name,
          content: note.content,
          date: new Date(),
        };
        this.notes.push(newNote);
        this.showAddForm = false;
        this.currentNote = newNote;
      },
      onRemoveNote: function (note){
        this.showAddForm = false;
        console.log(note, this.currentNote);
        if (note === this.currentNote){
          this.currentNote = null;
        }
        this.notes = this.notes.filter((n) => { return n !== note; });
      },
      onShowAddForm: function (){
        this.currentNote = null;
        this.showAddForm = true;
      },
      onShowNote: function (note){
        this.showAddForm = false;
        this.currentNote = note;
      }
    }
  };
</script>

<style>
  html, 
  body,
  #app {
	height: 100%;
  }

  .cover {
    background-image: url("./assets/background.jpg");
    background-position: center;
    background-size: cover;
    height: 30%;
  }
</style>