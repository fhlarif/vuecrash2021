<template>
  <div  v-on:dblclick ="$emit('toggle-reminder',task.id)" >

    <div class="grid grid-cols-1 bg-gray-300 md:grid-cols-2 " >
      <h3
        class="p-5 text-2xl text-green-800 bg-gray-100 border-4 border-opacity-75 rounded-br-full pb-9 border-light-blue-500" v-bind:class="[task.reminder ? 'bg-green-300':'','task']"
      >
        {{ task.text }}
        <p class="text-lg text-green-800">{{ task.day }}</p>
      </h3>

      <svg v-on:click="$emit('delete-task',task.id)"
        class="w-10 mb-7 md:w-12 place-self-end"
        viewBox="0 0 510 510"
        
        xmlns="http://www.w3.org/2000/svg"
      >

        <g id="XMLID_1473_">
          <path
            id="XMLID_1476_"
            d="m118.832 467.243c1.193 24.006 20.863 42.757 44.944 42.757h182.447c24.081 0 43.753-18.75 44.944-42.757l26.28-302.243h-324.895zm181.168-227.243h30v165h-30zm-60 0h30v165h-30zm-60 0h30v165h-30z"
          ></path>
          <path
            id="XMLID_1481_"
            d="m330 75v-30c0-24.812-20.186-45-45-45h-60c-24.812 0-45 20.188-45 45v30h-120v60h390v-60zm-120 0v-30c0-8.271 6.73-15 15-15h60c8.272 0 15 6.729 15 15v30z"
          ></path>
        </g>
      </svg>
        <span v-if="task.reminder" class="w-20 p-1 pl-2 pr-0 text-xs text-white bg-green-500 rounded animate-animate-ping-slow" >IMPORTANT</span>

    </div>
  </div>
</template>

<script>
export default {
  name: "Task",

  props: {
    task: Object,
  },

};
</script>