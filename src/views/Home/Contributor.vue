<template>
  <div class="col-md-6 mb-3">
    <div class="contributor shadow p-3 bg-white rounded">
      <ColorBox :color="contributor.color" />
      <div class="media mr-4">
        <img :src="contributor.avatarUrl" :alt="contributor.name + ' picture'" class="mr-3 rounded-circle" height="70px">
        <div class="media-body">
          <h5><a class="text-body" :href="ghLink">{{ contributor.name }}</a></h5>
          <p class="m-0"> Color code: <a :href="theColorApiLink" target="_blank">{{ contributor.color }}</a></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ColorBox from '@/components/ColorBox'

export default {
  name: 'Contributor',
  components: { ColorBox },
  props: {
    contributor: {
      required: true,
      type: Object
    }
  },
  computed: {
    theColorApiLink () {
      const noHashColor = this.contributor.color.substr(1)
      return `https://www.thecolorapi.com/id?format=html&hex=${noHashColor}`
    },
    ghLink () {
      return `https://github.com/${this.contributor.username}/`
    }
  }
}
</script>

<style lang="stylus">
.contributor
  position: relative

</style>
