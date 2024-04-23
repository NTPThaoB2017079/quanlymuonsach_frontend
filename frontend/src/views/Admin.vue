<template>
    <div class="admin-page">
        <welcome-admin v-if="showWelcome"></welcome-admin>
        <div class="vertical-menu">
            <router-link to="/manager/user-management" class="menu-item">
                <i class="fa-solid fa-user"></i>
                Người Dùng
            </router-link>
            <router-link to="/manager/book-management" class="menu-item">
                <i class="fa-solid fa-box"></i>
                Sách
            </router-link>
            <router-link to="/manager/borrow-censor" class="menu-item">
                <i class="fa-solid fa-dolly"></i>
                Mượn Sách
            </router-link>
            <router-link to="/" class="menu-item">
                <i class="fa-solid fa-house"></i>
                Về Trang Chính
            </router-link>
        </div>
        <router-view></router-view>
    </div>
</template>

<script>
import WelcomeAdmin from '../components/WelcomeAdmin.vue';
export default {
    components: {
        WelcomeAdmin
    },

    computed: {
        showWelcome() {
            const excludedRoutes = ['book-management',
                                'user-management', 'borrow-censor', 'add-book', 'book-form'];
            return !excludedRoutes.includes(this.$route.name);
        },
    }
}
</script>

<style>
.admin-page{
    display: flex;
    /* height:; */
}
.vertical-menu{
    width: 12%;
    border-right: 2px solid #1D24CA;
    font-weight: bold;
    height: 81vh;
    padding-top: 20px;
    font-family: 'Times New Roman', serif;
}

.menu-item:hover{
    text-decoration:underline 2px;
}

.menu-item {
    color: #1D24CA;
    text-decoration: none;
    height: 19vh;
    width: 100%;
    display: flex;
    align-items: center;
}

i{
    margin-left: 10px;
    margin-right: 10px;
}

</style>