<template>
    <div class="login_page">
        <div class="container">
            <form @submit.prevent="login" class="form">
                <h1>Đăng Nhập</h1>
                <div class="login_content">
                    <div class="login_box">
                        <i class="fa-solid fa-book-open-reader"></i>
                            <input v-model="formData.username" type="text" id="username" >
                            <label class="login_label">Username</label>
                    </div>
                    <div class="login_box">
                        <i class="fa-solid fa-lock"></i>
                            <input v-model="formData.password" type="password" id="username" >
                            <label class="login_label">Password</label>
                            <!-- <i class="fa-regular fa-eye" id="login-eye"></i>
                            <i class="fa-regular fa-eye-slash" id=""></i> -->
                    </div>
                </div>
                <div class="login_check">
                            <input type="checkbox" class="checkbox">
                            <label class="login_label">Lưu đăng nhập </label>
                            <router-link to="/">Quên mật khẩu</router-link>
                </div>
                <div><button type="submit" class="btn">Đăng nhập</button></div>
                <div class="login_register">
                    Bạn chưa có tài khoản? 
                    <router-link to="/register">Đăng ký</router-link>
                </div>

            </form>
        </div>
    </div>

</template>

<script>
import authService from '../services/auth.service';
import { toast } from 'vue3-toastify';
import 'vue3-toastify/dist/index.css';
export default {
    data() {
        return {
            formData: {
                username: '',
                password: '',
            },
        };
    },
    methods: {
        async login() {
            try {
                const response = await authService.login(this.formData)
                console.log(response)
                toast.success('Login successfully', {
                    autoClose: 800,
                })
                setTimeout(() => {
                    this.$router.push({name: 'home'})
                }, 1500);
            } catch (error) {
                console.log(error)
                toast.error('Username or password is incorrect', {
                    autoClose: 800,
                })
            }

        },
    },
};
</script>

<style scoped>
.login_page {
    font-family: 'Times New Roman', serif;
    height: 100vh;
    background-size: cover;
    display: grid;
    align-items: center;
    justify-content: center;
    background-image: url(../PictureProject/login_page.jpg);
    font-weight: bold;
}

.container {
    border: 2px solid none;
    justify-content: center;
    align-items: center;
    display: flex;
    /* background-color: aqua; */
    backdrop-filter: blur(15px);
    width: 400px;
    height: 450px;
    border-radius: 15px;
}

h1{
    text-align: center;
    font-weight: bold;
    color: #ECCA9C;
}

.login_box{
    position: relative;
    margin: 30px 0;
    width: 310px;
    border-bottom: 2px solid white;
}
.login_box label {
    position: absolute;
    top: 0%;
    left: 5px;
    transform: translateY(-50%);
    color: #7BC9FF;
    transition: 0.5s;
    pointer-events: none;
}
input:focus ~ label,
input:focus ~ :valid{
    top: -10px;
}

.login_box input {
    width: 100%;
    height: 30px;
    background: transparent;
    border: none;
    outline: none;
    padding: 0 35px 0 5px;
}

i{
    position: absolute;
    right: 8px;
    color: #7BC9FF;
    top: 0%;
}

.login_check {
    margin: -15px 0 15px;
    color: #7BC9FF;
    display: flex;
    justify-content: center;
}

.login_check a {
    text-decoration: none;
    color: #7BC9FF;
    margin-left: 30px;
}

.btn {
    width: 100%;
    border: 1px solid white;
    border-radius: 0px;
    font-weight: bold;
    color: #7BC9FF;
}
.login_register {
    justify-content: center;
    display: flex;
    margin: 10px;
    color: #7BC9FF;
}

.login_register a{
    margin-left: 20px;
    color: #7BC9FF;
}

.checkbox {
    margin-right: 5px;
}

.btn:hover {
    background-color: white;
    color: #009688;
    transition: 1s;
}
</style>
