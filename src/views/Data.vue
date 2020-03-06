<template>
    <div class="container">
        <div class="row align-items-center profile-header">

            <div class="col-md text-center text-md-left">
                <h2>{{ currTask.name }}</h2>
                <p class="lead text-muted">{{ currTask.details }}</p>
<!--                <p class="lead text-muted">{{ token }}</p>-->
            </div>
        </div>

    </div>
</template>
<script>

    export default {
        name: "home",
        props:['task'],
        data(){
            return {
                token: undefined,
                currTask: this.task
            }

        },

        methods: {
            getToken() {
                return this.token;
            }
        },
        mounted: function () {
            // eslint-disable-next-line no-console
            console.log('props', this.task)
        }

    };
</script>
