<template>
  <nav class="navbar navbar-expand navbar-dark bg-light">
    <a href="/admin" class="navbar-brand" v-if="this.local_user.role != 'user'"
      ><i class="fas fa-home"></i
    ></a>
    <!-- <div href="#" class="navbar-brand">Bánh Pía Đặc Sản Sóc Trăng</div> -->

    <div class="mr-auto navbar-nav">
      <li class="nav-item">
        <router-link to="/home" class="nav-link text-dark">
          TRANG CHỦ
        </router-link>
        <router-link
          to="/product"
          class="nav-link text-dark"
          v-if="this.local_user.role != 'admin'"
        >
          SẢN PHẨM
        </router-link>
        <router-link
          to="/introduce"
          class="nav-link text-dark"
          v-if="this.local_user.role != 'admin'"
        >
          GIỚI THIỆU
        </router-link>
      </li>
    </div>

    <img class="logo_login mr-auto" src="../assets/logo.png" alt="" />

    <div class="navbar-nav">
      <li class="nav-item">
        <router-link to="/shopping_cart" class="nav-link text-dark">
          <i class="fas fa-cart-shopping"></i>
          GIỎ HÀNG
        </router-link>
        <router-link
          to="/"
          class="nav-link text-dark"
          v-if="this.local_user.role != ''"
          @click="handleLogout"
        >
          ĐĂNG XUẤT
          <i class="fa-solid fa-right-from-bracket"></i>
        </router-link>
      </li>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      carts: [],
      local_user: {
        role: "",
      },
    };
  },
  methods: {
    logout() {
      localStorage.clear();
      this.$router.push({ name: "LoginPage" });
    },
    handleLogout() {
      localStorage.removeItem("user_login");
      this.$router.push({ name: "LoginPage" });
    },
  },
  mounted() {
    const listLoalCart = JSON.parse(localStorage.getItem("cart") ?? "[]");
    this.carts = listLoalCart;
    const user = JSON.parse(localStorage.getItem("user_login"));
    console.log(user);
    this.local_user = user;
  },
};
</script>

<style>
.logo_login {
  width: 140px;
  margin-right: 10px;
}

.navbar {
  top: 0;
  background-color: white;
}

.nav-link {
  float: left;
  font-size: 20px;
}
</style>
