<template>
    <div @dblclick="$emit('toggle-reminder', task.id)" 
    :class="[task.reminder ? 'border-l-4 border-green-700' : '', 'bg-gray-200 pl-3 py-1.5 cursor-pointer mx-3']">
        <h3 class="flex items-center justify-between font-bold">
            {{task.text}}
            <i @click="$emit('delete-task', task.id)"
            class="fas fa-times text-red-800 mr-2"> </i>
        </h3>
        <p>{{task.day}}</p>
    </div>
</template>

<script>
export default {
    name: 'Task',
    props: {
        task: Object,
    },
}
</script>
