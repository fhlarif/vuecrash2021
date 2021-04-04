<template>
   <header class="p-4 mt-6 bg-gray-700 border-4 border-opacity-75 pb-9 border-light-blue-500" >
     <div class="grid grid-cols-1 md:grid-cols-2 " >
    <h1 class="pl-1 pr-1 m-1 mt-5 text-5xl text-yellow-100 ">{{title}}</h1>
    <Button
    @btn-click="$emit('toggle-add-task')"
     class="p-2 mt-6 text-xl text-green-100 rounded-lg place-self-center sm:place-self-end animate-pulse "
     :text="showAddTask ? 'Close':'Add Task'" 
     :class="!showAddTask ? 'bg-green-500': 'bg-red-500' "
     
      />
    </div>
  </header>
</template>

<script>

import Button from "./Button";

export default {
    name: 'Header',
    props: {
    title: String,
    showAddTask:Boolean
    },

    components: {
    Button,
    }
}
</script>