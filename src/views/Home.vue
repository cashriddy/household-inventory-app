<template>
  <div class="home">
    <NewItem/>
    <ListItems/>
  </div>
</template>

<script>
// @ is an alias to /src
import NewItem from '@/components/NewItem.vue'
import ListItems from '@/components/ListItems.vue'

export default {
  name: 'home',
  components: {
    NewItem,
    ListItems
  }
}
</script>
