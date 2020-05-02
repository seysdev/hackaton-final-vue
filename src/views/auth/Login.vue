<template>
  <div class="view-login">
    <div class="image"></div>
    <div class="form">
      <h1>LOGIN</h1>
      <form @submit.prevent="handleSubmit" action="">
        <Input @input="(value) => (username = value)" placeholder="Usuario" label="Usuario" />
        <br />
        <Input
          @input="(value) => (password = value)"
          placeholder="Contraseña"
          label="Contraseña"
          type="password"
        />
        <br />
        <Button :fullWidth="true" type="primary">Ingresar</Button>
      </form>
    </div>
  </div>
</template>

<script>
import { mapActions, mapState } from 'vuex';
import Input from '@/components/Input.vue';
import Button from '@/components/Button.vue';

export default {
  name: 'Login',
  components: {
    Input,
    Button,
  },
  data() {
    return {
      username: '',
      password: '',
    };
  },
  watch: {
    isLogin(value) {
      if (value) {
        /* eslint-disable */
        alert('Bienvenido pase usted');
        this.$router.replace('/');
      } else {
        /* eslint-disable */
        alert('Usuario no encontrado!!');
      }
    },
  },
  computed: {
    ...mapState({
      isLogin: (state) => state.authStore.isLogin,
    }),
  },
  methods: {
    ...mapActions({
      login: 'authStore/login',
    }),
    handleSubmit() {
      this.login({
        username: this.username,
        password: this.password,
      });
    },
  },
};
</script>

<style lang="scss" scoped>
.view-login {
  display: flex;
  height: 100vh;

  .image {
    width: 60%;
    background: green;
  }

  .form {
    width: 40%;
    padding: 40px;
    align-self: center;
  }

  h1 {
    text-align: center;
    margin-bottom: 40px;
  }
}
</style>
