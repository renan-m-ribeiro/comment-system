<template>
    <div class="form-comment form-froup">
        <p>
            <input placeholder="name" type="text" name="author" class="form-control" v-model="name" />
        </p>
        <p>
            <textarea placeholder="comment" name="message" class="form-control" v-model="message" ></textarea>
        </p>
        <button v-on:click="addComment" class="btn btn-primary">Submit</button>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                name: "",
                message: ""
            }
        },
        methods: {
            addComment() {
                if(this.message.trim() === '') {
                    return alert('Please fill in the form!');
                }
                
                this.$emit('add-comment', {
                    name: this.name,
                    message: this.message
                });
                
                this.name = "";
                this.message = "";
            }
        }

    }
</script>