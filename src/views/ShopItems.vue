<template>
  <div class="card-group">
    <div class="col" v-for="shopitem in shopItems" :key="shopitem.id">
      <div class="card" @click="this.handleClickEvent(shopitem)">
        <img class="card-img-top" :src="shopitem.imagePath"
             :alt="shopitem.artikelName">
        <div class="card-body">
          <h5 class="card-title">{{ shopitem.artikelName }}</h5>
          <p class="card-text"><small class="text-muted">Last updated 3 mins ago</small></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ShopItems',
  data () {
    return {
      shopItems: []
    }
  },
  mounted () {
    const endpoint = ('http://localhost:8080/api/v1/shopitems')
    const requestOptions = {
      method: 'GET',
      redirect: 'follow'
    }

    fetch(endpoint, requestOptions)
      .then(response => response.json())
      .then(result => {
        this.shopItems = result
      })
      .catch(error => console.log('error', error))
  }
}
</script>

<style scoped>

</style>
