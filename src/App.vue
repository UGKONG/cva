<template>
  <main>
    <Header />
    <i :class="$store.state.Icon.stroke.v" />

    <router-view v-slot="{ Component, route }">
      <transition :name="route.meta.transition" mode="out-in">
        <component :is="Component" />
      </transition>
    </router-view>
  </main>
</template>

<script>
import { useComponent } from '@hook';

export default {
  name: 'App',
  components: {
    Header: useComponent(() => import('@/pages/Common/Header'))
  },
}
</script>

<style lang="scss" scoped>
@import '@index.scss';
main {
  @include flex(center, column);
  @include position(absolute, 50%, unset, unset, 50%, translate(-50%, -50%));

  @keyframes colorChange {
    0% {color: $darkGray}
    10% {color: $red}
    20% {color: $blue}
    30% {color: $green}
    40% {color: $black}
    50% {color: $orange}
    60% {color: $yellow}
    70% {color: $purple}
    80% {color: $pink}
    90% {color: $navy}
    100%{color: $darkGray;}
  }
  i {
    font-size: 40px;
    margin-bottom: 30px;
    transition: .2s;
    animation: colorChange infinite 10s;
  }
}
</style>
