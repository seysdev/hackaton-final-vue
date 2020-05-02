<template>
  <div class="view-register">
    <div class="image"></div>
    <div class="form">
      <h1>REGISTER</h1>
      <form @submit.prevent="handleSubmit" action="">
        <Input
          @input="(value) => (name = value)"
          :value="name"
          placeholder="Escriba aqui"
          label="Nombre y Apellido"
          required
        />
        <Input
          @input="(value) => (username = value)"
          :value="username"
          placeholder="Usuario"
          label="Usuario"
          required
        />
        <Input
          @input="(value) => (password = value)"
          :value="password"
          type="password"
          placeholder="Password"
          label="Password"
          required
        />
        <Input
          @input="(value) => (age = value)"
          :value="age"
          placeholder="Escriba aqui"
          label="Edad"
          required
        />
        <Input
          @input="(value) => (phone = value)"
          :value="phone"
          placeholder="Escriba aqui"
          label="Celular"
          required
        />
        <Input
          @input="(value) => (place = value)"
          :value="place"
          placeholder="Sede"
          label="Sede"
          required
        />
        <Input
          @input="(value) => (specialization = value)"
          :value="specialization"
          placeholder="Escriba aqui"
          label="Programa de especialización"
          required
        />
        <Button :fullWidth="true" type="primary">Registrar</Button>
      </form>
    </div>
  </div>
</template>

<script>
import { mapActions, mapState } from 'vuex';
import Input from '@/components/Input.vue';
import Button from '@/components/Button.vue';

export default {
  name: 'Register',
  components: {
    Input,
    Button,
  },
  data() {
    return {
      name: '',
      username: '',
      password: '',
      age: '',
      phone: '',
      place: '',
      specialization: '',
    };
  },
  watch: {
    successRegister(value) {
      if (value) {
        /* eslint-disable */
        alert('Tu registro fue correcto!!');
        this.$router.replace('login');
      } else {
        alert('Tu registro fue incorrecto, vuelve a intentarlo!!');
      }
    },
  },
  computed: {
    ...mapState('authStore', {
      successRegister: 'successRegister',
    }),
  },
  methods: {
    ...mapActions({
      register: 'authStore/register',
    }),
    handleSubmit() {
      this.register({
        name: this.name,
        username: this.username,
        password: this.password,
        age: this.age,
        phone: this.phone,
        place: this.place,
        specialization: this.specialization,
        firstTime: true,
      });
    },
  },
};
</script>

<style lang="scss" scoped>
.view-register {
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
