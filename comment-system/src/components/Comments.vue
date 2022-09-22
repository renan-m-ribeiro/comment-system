<template>
    <div class="container">
        <h1>Comments</h1>
        <hr />
        <FormComment v-on:add-comment="addComment" />
        <hr />
            <div class="list-group">
                <p>No comments...</p>
                <div class="list-group-item" v-for="comment, index in allComments">
                <span class="comment__author">Author: <strong>{{ comment.name }}</strong></span>
                <p>{{ comment.message }}</p>
                    <div>
                        <a href="#" title="Delete" v-on:click.prevent="removeComment(index)">Delete</a>
                    </div>
                </div>
            </div>
            <hr />
    </div>
</template>
<script>
    import FormComment from './FormComment.vue';
    export default {
        components: {
            FormComment
        },
        data() {
                return {
                    comments:[],
                }
        },
        methods: {
            addComment(comment) {
                this.comments.push(comment);
            },
            removeComment(index) {
                this.comments.splice(index, 1);
            }
        },
        computed: {
            allComments() {
                return this.comments.map(comment => ({
                    ...comment,
                    name: comment.name.trim() === '' ? 'Anonymous' : comment.name
                }))
            }
        },
        watch: {
            allComments(val) {
                console.log('val', val);
            }
        }
    }
</script>
