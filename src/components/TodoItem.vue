<template>
     <div style="display: flex; flex-direction: row; justify-content: center;">
      <p>{{numberList}}</p>
      <p>{{todo}}</p>
      <button @click="$emit('doneTodo', index)">Done</button>
    </div>
</template>

<script>
    export default {
        name: 'TodoItem',
        props: {
            todo: String,
            index: Number
        },
        computed: {
            numberList: function () {
                return this.index + 1
            }
        }
    }
</script>