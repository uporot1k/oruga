<template>
  <div>
    <o-field>
      <o-button size="medium" variant="primary" @click="openLoading">
        Launch loading
      </o-button>
    </o-field>
    <o-field>
      <o-switch v-model="isFullPage">Display loader over full page</o-switch>
    </o-field>
    <p style="position: relative" ref="element">
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce id
      fermentum quam. Proin sagittis, nibh id hendrerit imperdiet, elit sapien
      laoreet elit
    </p>
  </div>
</template>

<script>
import { defineComponent, ref } from 'vue'
import { useProgrammatic } from '@oruga-ui/oruga-next';

export default defineComponent({
  setup() {
    const { oruga } = useProgrammatic();

    const element = ref(null);
    const isFullPage = ref(true);

    function openLoading() {
      const loadingComponent = oruga.loading.open({
        fullPage: isFullPage.value,
        container: isFullPage.value ? null : element.value
      });

      setTimeout(() => loadingComponent.close(), 3 * 1000);
    }

    return {
      element,
      isFullPage,
      openLoading
    };
  },
});
</script>
