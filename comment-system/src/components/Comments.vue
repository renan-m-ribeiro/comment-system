<template>
    <div class="container">
        <h1>Comments</h1>
        <hr />
        <div class="form-comment form-froup">
        <p>
            <input placeholder="name" type="text" name="author" class="form-control" />
        </p>
        <p>
            <textarea placeholder="comment" name="message" class="form-control" ></textarea>
        </p>
        <button type="submit" class="btn btn-primary">Submit</button>
        </div>
        <hr />
            <div class="list-group">
                <div class="list-group-item" v-for="comment in comments">
                <span class="comment__author">Author: <strong>{{ comment.name }}</strong></span>
                <p>{{ comment.message }}</p>
                    <div>
                        <a href="#" title="Delete">Delete</a>
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
                    comments:[
                        {
                            name: "Ayrton",
                            message: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quae."
                        },
                    ]
                }
        }
    }
</script>
