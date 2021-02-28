<template>
    <div class="p-5">
        <h3 class="my-2 p-2 bg-light border text-center">
            <i class="bi-sticky text-secondary"></i> 
            {{note.name}}
        </h3>
        <div class="p-5 border border-1 rounded-0 text-center">{{note.content}}</div>
    </div>
</template>

<script>
export default {
    props: ['note'],
    data: function () {
      return {}
    },
    methods: {}
}
</script>