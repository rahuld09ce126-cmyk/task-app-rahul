<template>
    <div style="max-width: 600px; margin: auto">
        <h2>Task Manager</h2>

        <!-- Create Task -->
        <form @submit.prevent="createTask">
            <input
                v-model="form.title"
                placeholder="Task title"
                required
            />
            <select v-model="form.status">
                <option value="pending">Pending</option>
                <option value="in_progress">In Progress</option>
                <option value="completed">Completed</option>
            </select>
            <button type="submit">Add Task</button>
        </form>

        <hr />

        <!-- Task List -->
        <ul>
            <li v-for="task in tasks" :key="task.id">
                <strong>{{ task.title }}</strong>
                ({{ task.status }})

                <select v-model="task.status" @change="updateTask(task)">
                    <option value="pending">Pending</option>
                    <option value="in_progress">In Progress</option>
                    <option value="completed">Completed</option>
                </select>

                <button @click="deleteTask(task.id)">Delete</button>
            </li>
        </ul>

        <!-- Pagination -->
        <div style="margin-top: 10px">
            <button :disabled="!pagination.prev" @click="fetchTasks(pagination.prev)">
                Prev
            </button>
            <button :disabled="!pagination.next" @click="fetchTasks(pagination.next)">
                Next
            </button>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const tasks = ref([]);
const pagination = ref({ prev: null, next: null });

const form = ref({
    title: '',
    status: 'pending',
});

const fetchTasks = async (url = '/api/tasks') => {
    const response = await axios.get(url);
    tasks.value = response.data.data;
    pagination.value = {
        prev: response.data.links.prev,
        next: response.data.links.next,
    };
};

const createTask = async () => {
    await axios.post('/api/tasks', form.value);
    form.value.title = '';
    form.value.status = 'pending';
    fetchTasks();
};

const updateTask = async (task) => {
    await axios.put(`/api/tasks/${task.id}`, {
        status: task.status,
    });
};

const deleteTask = async (id) => {
    await axios.delete(`/api/tasks/${id}`);
    fetchTasks();
};

onMounted(fetchTasks);
</script>