<template>
  <transition name="fade">
    <div
      class="emoticon"
      v-show="input.emoticon"
      @click.stop=""
    >
      <div
        class="group"
        v-for="(group, index_1) in emoticon"
        :key="`group-${index_1}`"
      >
        <div
          class="item"
          v-for="(item, index_2) in group"
          @click="handelEmoticonClick(item)"
          :title="item.title"
          :key="index_2"
        >
          <img
            :src="item.url"
            :alt="item.title"
          />
        </div>
      </div>
    </div>
  </transition>
</template>

<script lang="ts" setup>
import { emoticon } from '@/assets/data/emoticon'
import { input } from '@/store/input'

const emit = defineEmits<{
  (event: 'emoticon', url: string, name: string): void
}>()

const handelEmoticonClick = (item: Emoticon) => {
  if (item.base64) {
    const img = new Image()
    img.onload = function () {
      const canvas = document.createElement('canvas')
      canvas.width = img.width
      canvas.height = img.height
      const ctx = canvas.getContext('2d')
      ctx?.drawImage(img, 0, 0)
      const baseData = canvas.toDataURL('image/png')

      emit('emoticon', baseData, item.title)
    }
    img.src = item.url
  } else {
    emit('emoticon', item.url, item.title)
  }
}
</script>

<style lang="stylus" scoped>
.emoticon
  overflow auto
  position absolute
  right 50px
  bottom 180px
  width 1200px
  height 800px
  background #fff
  padding 20px
  border-radius 5px
  box-shadow 0 0 20px 5px rgba(0, 0, 0, 0.15)
  user-select none

  .group
    display flex
    flex-wrap wrap
    padding 20px

    .item
      width calc(20% - 10px)
      margin 5px
      cursor pointer

      img
        width 100%
</style>
