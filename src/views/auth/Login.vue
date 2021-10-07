<template>
    <div class="container">
        <div class="row">
            <div class="col-5">
                <div class="card">
                    <div class="card-body">
                        <form action="">
                            <label class="form-label" for="email">E-mail</label>
                            <input class="form-control" type="text" v-model="form.email" id="email">
                            <label class="form-label" for="pass">Contraseña</label>
                            <input class="form-control" type="password" v-model="form.password" id="pass">
                            <input class="btn btn-primary mt-2" type="button" @click="login" value="Ingresar">
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return {
            form: {
                email: '',
                password: ''
            }
        }
    },
    methods: {
        login(){
            let formData = new URLSearchParams()
            formData.append('email', this.form.email)
            formData.append('password', this.form.password)
            axios.post('https://mintic-88.herokuapp.com/login', formData, {
                headers: {
                    "Access-Control-Allow_Methods": "POST"
                }
            })
            .then((response)=>{
                // console.log(response.data)
                localStorage.setItem('token', response.data.token)
                this.$router.push('/home')
            })
            // if(this.user){
            //     localStorage.setItem('user', this.user);
            //     this.$router.push('/home');
            // }
        }
    }
}
</script>