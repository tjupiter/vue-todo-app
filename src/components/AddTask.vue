<template>
    <form @submit="onSubmit" action="#"
    class=" bg-gray-100 p-3">
        <div>  
            <div class="space-y-1">
                <label class="text-lg font-bold ml-1">Task</label>
                <input 
                type="text"
                v-model="text"
                name="text"
                placeholder="Add New Task"
                class="block rounded-lg pl-3 py-2 w-full"
                />
            </div>
            
            <div class="space-y-1 mt-3">
                <label class="text-lg font-bold ml-1">Day & Time</label>
                <input 
                type="text"
                v-model="day"
                name="day"
                placeholder="Add Day & Time"
                class="block rounded-lg pl-3 py-2 w-full"
                />
            </div>
            
            <div class="mt-3 ml-1 flex items-center">
                <label class="mr-2">Set Reminder</label>
                <input type="checkbox" v-model="reminder" name="reminder" />
            </div>

             <input 
                class="border rounded-md py-2 px-3 bg-black shadow text-white w-full mt-3 hover:bg-gray-800"
                type="submit" value="Save Task">
        </div>

      
    </form>
</template>

<script>
export default {
    name: 'AddTask',
    data() {
        return {
            text: '',
            day: '',
            reminder: false
        }
    },

    methods: {
        onSubmit(e) {
            e.preventDefault()

            if(!this.text) {
                alert('Please add task')
                return
            }

            const newTask = {
                id: Math.floor(Math.random() * 100000),
                text: this.text,
                day: this.day,
                reminder: this.reminder
            }

            this.$emit('add-task', newTask)

            this.text = ''
            this.day = ''
            this.reminder = false 


        }
    }
}
</script>
