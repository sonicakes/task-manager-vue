<template>
<form @submit="onSubmit" class="py-3">
  <div class="mb-3">
    <label for="taskName" class="form-label">Task name:</label>
    <input v-model="text" type="text" class="form-control" id="taskName">
  </div>
  <div class="mb-3">
    <label for="dayTime" class="form-label">Add day and time:</label>
    <input v-model="day" type="text" class="form-control" id="dayTime">
  </div>
  <div class="mb-3 form-check">
    <input v-model="reminder" type="checkbox" class="form-check-input" id="reminder">
    <label class="form-check-label" for="reminder">Set reminder?</label>
  </div>
  <button type="submit" class="btn btn-primary">Save task</button>
</form>
</template>

<script>
export default {
    name: "AddTask",
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
                alert ('please add a task');
                return;
            }
            const newTask = {
                id: Math.floor(Math.random() * 100000),
                text: this.text,
                day: this.day,
                reminder: this.reminder
            }

            this.$emit('add-task', newTask);

            this.text = ""
            this.day = ""
            this.reminder = false
        }
    }
}
</script>