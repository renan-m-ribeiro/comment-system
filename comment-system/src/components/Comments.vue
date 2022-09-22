<template>
    <div class="container">
        <h1>Comments</h1>
        <hr />
        <div class="form-comment form-froup">
        <p>
            <input placeholder="name" type="text" name="author" class="form-control" v-model="name" />
        </p>
        <p>
            <textarea placeholder="comment" name="message" class="form-control" v-model="message" ></textarea>
        </p>
        <button v-on:click="addComment" class="btn btn-primary">Submit</button>
        </div>
        <hr />
            <div class="list-group">
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
    export default {
        data() {
                return {
                    comments:[],
                    name: "",
                    message: ""
                }
        },
        methods: {
            addComment() {
                if(this.message.trim() === '') {
                    return alert('Please fill in the form!');
                }
                this.comments.push({
                    name: this.name,
                    message: this.message
                });
                
                this.name = "";
                this.message = "";
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
        }
    }
</script>
