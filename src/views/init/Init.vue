<template>
  <div class="view-init">
    <h1>Cuentanos Sobre ti</h1>
    <form v-if="firsTime" @submit.prevent="handleSubmit" action="">
      <Input
        @input="(value) => (profile = value)"
        :value="profile"
        placeholder="Perfil"
        label="PERFIL"
        required
      />
      <Input
        @input="(value) => (phone = value)"
        :value="phone"
        placeholder="Escriba aqui"
        label="Celular"
        required
        disabled
      />
      <Input
        @input="(value) => (place = value)"
        :value="place"
        placeholder="Sede"
        label="Sede"
        required
        disabled
      />
      <Input
        @input="(value) => (specialization = value)"
        :value="specialization"
        placeholder="Escriba aqui"
        label="Programa de especialización"
        required
        disabled
      />
      <Input
        @input="(value) => (email = value)"
        :value="email"
        placeholder="Correo Electronico"
        label="Correo Electronico"
        required
      />
      <Button :fullWidth="true" type="primary">Registrar</Button>
    </form>
    <div v-else>
      No es tu primera vez!!
    </div>
  </div>
</template>

<script>
import { mapState, mapMutations } from 'vuex';
import { SET_USER } from '@/views/auth/store/mutatios-type';
import Input from '@/components/Input.vue';
import Button from '@/components/Button.vue';

export default {
  name: 'Init',
  components: {
    Input,
    Button,
  },
  data() {
    return {
      profile: '',
      phone: '',
      place: '',
      specialization: '',
      email: '',
      id: '',
      firsTime: true,
    };
  },
  computed: {
    ...mapState({
      user(state) {
        console.log('state.authStore.user', state.authStore.user);
        this.phone = state.authStore.user.phone;
        this.place = state.authStore.user.place;
        this.specialization = state.authStore.user.specialization;
        this.id = state.authStore.user.id;
        this.firsTime = state.authStore.user.firsTime;
      },
    }),
  },
  watch: {
    user(user) {
      console.log('user', user);
    },
  },
  methods: {
    ...mapMutations({
      setUser: `authStore/${SET_USER}`,
    }),
    handleSubmit() {
      fetch(`http://localhost:3000/users/${this.id}`, {
        method: 'PATCH',
        body: JSON.stringify({
          firsTime: false,
          profile: this.profile,
          email: this.email,
        }),
        headers: {
          'Content-type': 'application/json; charset=UTF-8',
        },
      })
        .then((response) => response.json())
        .then((user) => this.setUser(user));
    },
  },
};
</script>

<style></style>
