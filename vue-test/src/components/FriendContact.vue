<template>
    <li>
        <h2>{{ name }} {{ isFavorite ? "(Favorite)" : '' }}</h2>
        <button @click="toggleDetails"> {{ detailsAreVisible ? 'Hide Details' : 'Show Details' }}</button>
        <button @click="toggleFavorite"> Toggle Favorite</button>

        <ul v-if="detailsAreVisible">
            <li><strong>Phone: </strong>{{ phoneNumber }}</li>
            <li><strong>Email: </strong>{{ emailAddress }}</li>
        </ul>
    </li>
</template>

<script>
export default {
    // props: ['name', 'phoneNumber', 'emailAddress','isFavorite'],
    props: {
        id: {
            type: String,
            required: true
        },
        name: {
            type: String,
            required: true
        },
        phoneNumber: {
            type: String,
            required: true
        },
        emailAddress: {
            type: String,
            required: true
        },
        isFavorite: {
            type: Boolean,
            required: false,
            default: false
        }

    },
    emits: ['toggle-favorite'],
    data () {
        return {
            detailsAreVisible: false,

        }
    },
    methods: {
        toggleDetails () {
            this.detailsAreVisible = !this.detailsAreVisible
        },
        toggleFavorite () {
            // this.friendIsFavorite =!this.friendIsFavorite
            this.$emit('toggle-favorite', this.id)
            console.log(`inside${this.id}`)
        }
    },
}
</script>