<template>
    <div class="container">
        <nav class="navbar sticky-top navbar-light bg-light">
            <div class="container-fluid">
                <a class="navbar-brand" href="#">Sticky top</a>
            </div>
        </nav>
        <UsersTable v-if="false" :users="users"></UsersTable>
        <users v-bind:users="users"></users>
    </div>
</template>

<script>
import api from '@/api';
import Users from '@/components/Users.vue';
import UsersTable from '@/components/UsersTable';

export default {
    name: 'Home',
    components:{
        Users,
        UsersTable
    },
    data(){
        return {
            users:[]
        }
    },
    created(){
        // api.getUsersPromise().then(data => console.log(data));
        api.getUsersPromise().then(data => this.users = data);
        // ( async ()=>{ 
        //     this.users = await api.getUsersAsync(); 
        //     console.log(this.users);
        // })();
    }
}
</script>