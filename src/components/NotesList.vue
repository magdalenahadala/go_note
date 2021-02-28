<template>
    <div class="p-3 h-75">
      <h3>My notes</h3>
      <div v-if="notes.length > 0" class="h-100 overflow-auto">
        <div v-for="note in notes" v-bind:key="note.id" class="border bg-white p-2 my-2">
          <div class="text-end">
            <div class="btn-group" role="group">
              <button v-on:click="onRemove(note)" type="button" class="btn btn-outline-danger">
                <i class="bi-trash-fill"></i>
              </button>
              <button v-on:click="onShow(note)" type="button" class="btn btn-outline-secondary">
                <i class="bi-eye-fill"></i>
              </button>
            </div>
          </div>
          <div class="text-center">
            {{note.name}}
            <small class="text-muted">({{note.date}})</small>
          </div>
        </div>
      </div>
      <div v-else class="alert alert-secondary" role="alert">
        Oopsss! No notes to display.
      </div>
    </div>
</template>

<script>
export default {
    props: ['notes'],
    data: function (){ return {}},
    methods: {
        onRemove: function (note){
          this.$emit('note-remove', note);
        },
        onShow: function (note){
          this.$emit('note-show', note);
        }
    }
}
</script>