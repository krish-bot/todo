<template>
  <tr>
      <td class="w-50 text-left"><button @click.self="$emit('complete')" :class="className">
          <i class="far fa-circle"></i>{{ todo.title }}
          </button>
      </td>
      <td class="w-25 text-left">{{ todo.time }}</td>
      <td class="w-25 text-left">{{todo.date}}</td>
      <td class="w-25"><button @click="$emit('remove')"><i class="far fa-trash-alt"></i></button></td>
  </tr>   
</template>

<script>
export default {
  name: "TaskItem", 
  props: ["todo"],
  computed: {
    className() {
      let classes = ['toggle'];
      if(this.todo.completed) {
        classes.push('toggle-completed');
      }
      return classes.join(' ');
    }
  }
};
</script>