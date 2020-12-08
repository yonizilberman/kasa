<template>
  <div class="cardThumbnail h-mb-24" :class="{'h-m-24': thumbnailPositionTop}">
    <div v-if="!hideAvatar" class="avatar">
      <img :src="cardTextContent.url" />
    </div>
    <div>
      <h3 v-if="cardTextContent.title">{{ cardTextContent.title }}</h3>
      <p v-if="cardTextContent.subtitle">{{ cardTextContent.subtitle }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardThumbnail',
  props: {
    cardTextContent: {
      type: Object,
      default: () => ({
        url: '',
        title: '',
        subtitle: ''
      })
    },
    hideAvatar: {
      type: Boolean,
      default: false
    },
    thumbnailPositionTop: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="scss" scoped>
.cardThumbnail {
  height: 60px;
  display: flex;
  flex-direction: row;
  .avatar > img {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    object-fit: cover;
    }
  & > div:first-child {
    padding: 0 24px 0 0;
  }
  & > div:last-child {
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  h3 {
    font-family: lora, Avenir, Helvetica, Arial, sans-serif;
    font-size: 20px;
    font-weight: bold;
  }
  p {
    font-size: 14px;
    font-weight: medium;
    color: #6E6E6E;
  }
}</style>