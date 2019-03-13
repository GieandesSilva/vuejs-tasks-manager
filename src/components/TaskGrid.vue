<template>
    <div class="task-grid">
        <template v-if="tasks.length">
            <div v-for="(task, i) in tasks" :key="task.name">
                <Task :task="task" @taskDeleted="$emit('taskDeleted', i)"  @alterStatusTask="$emit('alterStatusTask', i, $event)" />
            </div>
        </template>
        <CompletedTasks v-else />
    </div>
</template>

<script>
import Task from '@/components/Task'
import CompletedTasks from '@/components/CompletedTasks'
export default {
    components: { Task, CompletedTasks },
    props: { tasks: Array, required: true }
}
</script>

<style>

    .task-grid {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }

    .task-grid .task {
        margin: 10px;
    }
    
</style>
