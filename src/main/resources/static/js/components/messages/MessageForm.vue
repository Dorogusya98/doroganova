<template>

    <v-layout>
        <v-textarea
                background-color="green lighten-4"
                color="cyan"
                label="New recipe"
                filled
                auto-grow
                v-model="text"
        ></v-textarea>
        <v-btn @click="save" color="green lighten-2" class="mx-2">
            Save
        </v-btn>
    </v-layout>
</template>

<script>
    import { mapActions } from 'vuex'
    export default {
        props: ['messageAttr'],
        data() {
            return {
                text: '',
                id: null
            }
        },
        watch: {
            messageAttr(newVal, oldVal) {
                this.text = newVal.text
                this.id = newVal.id
            }
        },
        methods: {
            ...mapActions(['addMessageAction', 'updateMessageAction']),
            save() {
                const message = {
                    id: this.id,
                    text: this.text
                }
                if (this.id) {
                    this.updateMessageAction(message)
                } else {
                    this.addMessageAction(message)
                }
                this.text = ''
                this.id = null
            }
        }
    }
</script>

<style>
</style>