<template>
    <div class="homepage">
        <div class="content">
            <h1>Quản lý sách</h1>
            <p>Một quyển sách hay là đời sống xương máu quý giá của một tinh thần ướp hương và cất kín cho mai sau
            <br> Vui lòng đăng nhập để cùng nhau khám phá</p>
            <div>
                <button>
                    <span></span>
                    <router-link to="/login">Đăng Nhập</router-link>
                </button>
                <button>
                    <span></span>
                    <router-link to="/register">Đăng Ký</router-link>
                </button>
            </div>
        </div>
    </div>
</template>

<script>


export default {
    name: 'Home',
}

</script>

<style>
    .homepage{
        width: 100%;
        height: 100vh;
        background-image: url('../PictureProject/homepage.jpg');
        opacity: 0.6;
        position: relative;
        font-family: 'Times New Roman', serif;
    }

    .homepage p {
        color: burlywood;
        font-size: 20px;
    }

    .logo {
        font-family: 'Times New Roman', serif;;
        font-size: 60px;
        cursor: pointer;
        color: #0C359E;
    }

    .navbar ul li{
        list-style: none;
        display: inline-block;
        margin: 0 20px;
        position: relative;
    }

    .navbar ul li a{
        text-decoration: none;
        color: #0C359E;
        text-transform: uppercase;
        font-weight: bold;
    }

    
    .navbar ul li::after{
        content: '';
        height: 3px;
        width: 0;
        background: white;
        position: absolute;
        left: 0;
        bottom: -10px;
        transition: 0.5s;
    }

    .navbar ul li:hover::after{
        width: 100%;
    }

    .content {
        width: 100%;
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
        text-align: center;
        color: #fff;

    }

    .logo h1{
        font-size: 70px;
        color: #0C359E;
        font-weight: bold;
    }

    .content h1{
        font-size: 70px;
        margin-top: 80px;
    }

    .content p{
        margin: 20px auto;
        font-weight: 100;
        line-height: 25px;
        font-weight: bold;
    }

    button{
        width: 200px;
        padding: 10px 5px;
        text-align: center;
        margin: 20px 10px;
        border-radius: 5px;
        font-weight: bold;
        border: 2px solid #0C359E;
        background: transparent;
        color: white;
        cursor: pointer;
        position: relative;
        overflow: hidden;
        font-family: 'Times New Roman', serif;
        font-size: 20px;
    }
    span{
        background: #0C359E;
        height: 100%;
        width: 0;
        border-radius: 5px;
        position: absolute;
        left: 0;
        bottom: 0;
        z-index: -1;
        transition: 0.5s;
    }

    button:hover span {
        width: 100%;
    }
    button:hover{
        border: none;
    }

    button a{
        text-decoration: none;
        color: #fff;
    }
</style>