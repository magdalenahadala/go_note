<template>
    <div class="h-100">
        <div class="text-end">
            <button v-on:click="onRemove()" type="button" class="btn btn-outline-danger">
                <i class="bi-trash-fill"></i>
            </button>
        </div>
        <h3 class="my-2 p-2 bg-light border text-center">
            <i class="bi-sticky text-secondary"></i> 
            {{note.name}}
        </h3>
        <div class="p-5 border border-1 rounded-0 text-center h-75 overflow-auto">{{note.content}}</div>
    </div>
</template>

<script>
export default {
    props: ['note'],
    data: function () {
      return {}
    },
    methods: {
        onRemove: function (){
          this.$emit('note-remove', this.note);
        },
    }
}
</script>