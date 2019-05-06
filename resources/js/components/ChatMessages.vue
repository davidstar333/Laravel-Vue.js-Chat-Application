<template>
    <ul class="chat">
        <li class="clearfix" v-for="(message,i) in messages" :key="i">
            <div class="chat-body clearfix" :class="(message.user.id == userId) ? 'my-chat-body right' : null">
                <div class="header">
                    <strong class="primary-font">
                        {{ message.user.name }}
                    </strong>
                </div>
                <p>
                    {{ message.message }}
                </p>
            </div>
        </li>
    </ul>
</template>

<script>
export default {
    props: ['messages'],
    data() {
        return {
            userId: '',
            myMsg: false
        }
    },
    created() {
        this.userId = Laravel.user.id;
        document.getElementById('message').scrollTop = document.getElementById('message').scrollHeight;
    },
    updated() {
        document.getElementById('message').scrollTop = document.getElementById('message').scrollHeight;
    }
};
</script>