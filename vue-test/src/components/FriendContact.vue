<template>
    <li>
        <h2>{{ friend.name }}</h2>
        <button @click="toggleDetails"> {{ detailsAreVisible ? 'Hide Details' : 'Show Details' }}</button>
        <ul v-if="detailsAreVisible">
            <li><strong>Phone: </strong>{{ friend.phone }}</li>
            <li><strong>Email: </strong>{{ friend.email }}</li>
        </ul>
    </li>
</template>

<script>
export default {
    data () {
        return {
            detailsAreVisible: false,
            friend: {
                id: 'radhi',
                name: 'radhi hudijan',
                phone: "012238070",
                email: "radhi@fff.com"
            }
        }
    },
    methods: {
        toggleDetails () {
            this.detailsAreVisible = !this.detailsAreVisible
        }
    },
}
</script>