<template>
  <div class="home">
    <Loading :width="200" :height="200" v-if="loading">
      <div>加载中。。。。。。。。。。</div>
    </Loading>

    <Container :options="{ width: 1536, height: 722 }" v-else>
      <div style="width:1000px">
        <FlyBox>
          <div>
            <div>sadfsaf</div>
          </div>
        </FlyBox>
      </div>
    </Container>
  </div>
</template>

<script>
import { ref } from 'vue'
export default {
  name: 'Home',

  components: {
  },
  setup (ctx) {
    const loading = ref(true)
    setTimeout(() => {
      loading.value = false
    }, 3000)
    return {
      loading
    }
  }
}
</script>
<style lang="scss" scoped>
.home {
  background: #000;
}
</style>
