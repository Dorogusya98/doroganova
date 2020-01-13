<template>
    <v-layout class="px-3">
        <v-textarea
                filled
                auto-grow
                label="Write comment"
                color="green lighten-2"
                background-color="green lighten-4"
                row-height="10"
                v-model="text"
                @keyup.enter="save"></v-textarea>
        <v-btn @click="save" color="green lighten-2" class="mx-2">
            Add
        </v-btn>
    </v-layout>
</template>

<script>
    import { mapActions } from 'vuex'
    export default {
        name: 'CommentForm',
        props: ['messageId'],
        data() {
            return {
                text: ''
            }
        },
        methods: {
            ...mapActions(['addCommentAction']),
            async save() {
                await this.addCommentAction({
                    text: this.text,
                    message: {
                        id: this.messageId
                    }
                })
                this.text = ''
            }
        }
    }
</script>

<style scoped>
</style>