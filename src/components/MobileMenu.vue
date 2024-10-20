<template>
  <transition name="slide-fade">
    <div class="mobile-menu" v-if="isOpen">
      <ul class="mobile-menu__list">
        <li class="mobile-menu__item">
          <router-link @click="closeMenu" to="/">Home</router-link>
        </li>
        <li class="mobile-menu__item">
          <router-link @click="closeMenu" to="/impacto-ambiental">Impacto Ambiental</router-link>
        </li>
        <li class="mobile-menu__item">
          <router-link @click="closeMenu" to="/tipos-de-moda">Tipos de Moda</router-link>
        </li>
        <li class="mobile-menu__item">
          <router-link @click="closeMenu" to="/bauru">Bauru</router-link>
        </li>
        <li class="mobile-menu__item">
          <router-link @click="closeMenu" to="/sujeito">Sujeito</router-link>
        </li>
      </ul>
    </div>
  </transition>
</template>

<script>
export default {
  props: {
    isOpen: {
      type: Boolean,
      required: true,
    },
  },
  methods: {
    closeMenu() {
      this.$emit('close-menu'); // Emite o evento para o componente pai
    },
  },
};
</script>

<style scoped>
.mobile-menu {
  background-color: #efefef;
  width: 100%;
  position: absolute;
  top: 80px;
  left: 0;
  padding: 20px;
  z-index: 10;
  border-radius: 0 0 10px 10px;
}

/* Lista do menu */
.mobile-menu__list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.mobile-menu__item {
  margin-bottom: 20px;
}

.mobile-menu__item a {
  text-decoration: none;
  color: #333;
  font-size: 18px;
}

/* Transições */
.slide-fade-enter-active, .slide-fade-leave-active {
  transition: all 0.3s ease;
}

.slide-fade-enter-from {
  transform: translateY(-20px);
  opacity: 0;
}

.slide-fade-enter-to {
  transform: translateY(0);
  opacity: 1;
}

.slide-fade-leave-from {
  transform: translateY(0);
  opacity: 1;
}

.slide-fade-leave-to {
  transform: translateY(-20px);
  opacity: 0;
}
</style>
