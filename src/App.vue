<template>
    <div id="app">
        <bodong-header></bodong-header>
        <bodong-input v-on:addUser="addUser"></bodong-input>
        <bodong-list v-bind:propsdata="users" v-on:removeUser="removeUser"></bodong-list>
        <bodong-footer v-on:clearUsers="clearUsers"></bodong-footer>
    </div>
</template>

<script>
    import BodongHeader from './components/BodongHeader'
    import BodongInput from './components/BodongInput'
    import BodongList from './components/BodongList'
    import BodongFooter from './components/BodongFooter'

    import { API } from './components/Constants'

    import axios from 'axios'

    export default {
        data() {
            return {
                users: []
            }
        },
        created() {
            const app = this;
            axios.get(API.HOST + '/users').then(function ({data}) {
                for (var i = 0; i < data.length; i++) {
                    app.users.push(data[i]);
                }
            });
        },
        methods: {
            addUser(userId) {
                axios.post(API.HOST + '/users', {
                    id: userId
                }).then(({data}) => {
                    this.users.push({no: data, id: userId});
                });
            },
            removeUser(user, index) {
                const app = this;
                axios.delete(API.HOST + '/users/' + user.no).then(() => {
                    app.users.splice(index, 1);
                });
            },
            clearUsers() {
                this.users = [];
            }
        },
        components: {
            'BodongHeader': BodongHeader,
            'BodongInput': BodongInput,
            'BodongList': BodongList,
            'BodongFooter': BodongFooter
        }
    }
</script>

<style>
    body {
        text-align: center;
        background-color: #F6F6F8;
    }

    input {
        border-style: groove;
        width: 200px;
    }

    button {
        border-style: groove;
    }

    .shadow {
        box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03)
    }
</style>
