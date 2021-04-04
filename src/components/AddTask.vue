<template>
  <div class="">
    <form
    @submit="onSubmit"
      class="w-full px-3 py-4 mx-auto text-center text-white rounded bg-blue"
    >
      <label for="text" class="flex justify-center mb-1 bg-green-400 border-2 border-green-100"
        >Task
      </label>
      <input
      v-model="text"
        name="text"
        type="text"
        placeholder="Add Task"
        class="block w-full px-3 py-2 mx-auto text-sm text-blue-800 rounded"
      />

      <label for="day" class="flex justify-center mt-4 mb-1 bg-green-400 border-2 border-green-100"
        >Day/Time
      </label>

      <input
      v-model="day"
        name="day"
        type="text"
        placeholder="Add Day & Time"
        class="block w-full px-3 py-2 mx-auto mb-4 text-sm text-blue-800 rounded"
      />
        <div class="grid grid-cols-2 mb-4">
       <label for="reminder" class="flex justify-center bg-green-400 border-2 border-green-100"
        >Set Reminder
      </label>

      <input
      v-model="reminder"
        name="reminder"
        type="checkbox"
        placeholder="Add Day & Time"
        class="block w-6 text-blue-800 rounded place-self-center "
      />
      </div>

      <button
        class="block w-full px-4 py-2 mx-auto font-bold text-white bg-blue-500 border rounded"
      >
        Save Task
      </button>
    </form>
  </div>
</template>

<script>
export default {
  name: "AddTask",

  data(){
      return{
          text:'',
          day:'',
          reminder:false,
      }
  },
  methods: {
      onSubmit(e){
          e.preventDefault();
          if(!this.text){
              alert('Please add a task')
              return
          }

          const newTask ={
              id: Math.floor(Math.random()*100000),
              text: this.text,
              day: this.day,
              reminder: this.reminder

          }

          this.$emit('add-task',newTask)
          this.text = ""
          this.day =""
          this.reminder =false
      }
  }
};
</script>