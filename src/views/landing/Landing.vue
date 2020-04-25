<template>
  <div class="view-landing">
    <h1>Explota todo tu potencial tecnologico</h1>
    <p>Con nuestros programas de especializcion</p>
    <Button v-on:onclick="register" type="primary">Registrate</Button>
    <Button v-on:onclick="sigin" type="ghost">Ingresar</Button>
  </div>
</template>

<script>
import Button from '@/components/Button.vue';

export default {
  name: 'Landing',
  components: {
    Button,
  },
  methods: {
    register() {
      console.log('register!!');
    },
    sigin() {
      console.log('sigin!!');
    },
  },
};
</script>

<style lang="scss"></style>
