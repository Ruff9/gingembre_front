<template>
    <div class="user-index-container">
        <section class="user-list">
            <div v-for="user in users" class="user-link-name">
                <span>{{ user.username }}</span>
            </div>
        </section>
    </div>
</template>

<script>
    import axios from 'axios'

    export default {
        data() {
            return {
                users: ['']
            }
        },
        methods: {
            async getData() {
                try {
                    const path = import.meta.env.VITE_BACKEND_URL + '/api/users/';
                    const response = await axios.get(path);
                    this.users = response.data;
                } catch (error) {
                    console.log(error);
                }
            },
        },
        created() {
            this.getData();
        }
    }
</script>