<template>
  <div id="app">
    <!-- loader with avatar -->
    <Card :cardTextContent="{}"></Card>

    <!-- loader without avatar -->
    <Card hideAvatar :cardTextContent="{}" ></Card>

    <Card
      hideAvatar
      :cardTextContent="cardTextContent1"
      @clickhendle="handleCilck"
    >
    <template #body>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
    </template>
    <template #footer>
      handle clck for a alert
    </template>
    </Card>

    <Card
      :cardTextContent="cardTextContent2"
      @clickhendle="handleCilckForLink"
    >
    <template #body>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
    </template>
    <template #footer>
      handle cilck for link
    </template>
    </Card>

    <Card
      thumbnailTop
      :cardTextContent="cardTextContent"
      @clickhendle="cardTextContentFun"
    >
    <template #body>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
    </template>
    <template #footer>
      Card footer
    </template>
    </Card>

    <Card
      thumbnailTop
      :cardTextContent="cardTextContent"
      @clickhendle="cardTextContentFun"
    >
    <template #body>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
    </template>
    </Card>

    <Card
      hideCover
      :cardTextContent="cardTextContent"
      @clickhendle="cardTextContentFun"
    >
    <template #body>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
    </template>
    <template #footer>
      Card footer
    </template>
    </Card>

    <Card
      hideCover
      :cardTextContent="cardTextContent"
      @clickhendle="cardTextContentFun"
    >
    <template #body>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
    </template>
    </Card>

    <Card
      :cardTextContent="cardTextContent"
      @clickhendle="cardTextContentFun"
    >
    <template #body>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
    </template>
    </Card>

    <Card
      size="l"
      :cardTextContent="{url: require('@/assets/room.svg'), title: 'Card Title', subtitle: 'Card Subtitle'}"
      @clickhendle="cardTextContentFun"
    >
    <template #body>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
    </template>
    <template #footer>
      Card footer
    </template>
    </Card>

    <Card
      size="xl"
      :cardTextContent="{url: require('@/assets/room.svg'), title: 'Card Title', subtitle: 'Card Subtitle'}"
      @clickhendle="cardTextContentFun"
    >
    <template #body>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
    </template>
    <template #footer>
      Card footer
    </template>
    </Card>

    <Card
      size="xl"
      :cardTextContent="{url: require('@/assets/room.svg'), title: 'Card Title', subtitle: 'Card Subtitle'}"
      @clickhendle="cardTextContentFun"
    >
    <template #body>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
    </template>
    </Card>
  </div>
</template>

<script>
import Card from './components/Card.vue'

export default {
  name: 'App',
  mounted () {
    setTimeout(() => {
      this.cardTextContent1 = {
        url: require('@/assets/room.svg'),
        title: 'Card Title',
        subtitle: 'Card Subtitle'
      }

      this.cardTextContent2 = {
        url: require('@/assets/room.svg'),
        title: 'Card Title',
        subtitle: 'Card Subtitle'
      }
    }, 3000)
  },
  methods: {
    handleCilckForLink () {
      window.open("https://kasa.com/", "_blank")
    },
    handleCilck () {
      alert('card got click')
    },
    cardTextContentFun (cardTextContent) {
      console.log(`click: `, cardTextContent)
    }
  },
  data () {
    return {
      cardTextContent: {
        url: require('@/assets/room.svg'),
        title: 'Card Title',
        subtitle: 'Card Subtitle'
      },
      cardTextContent1: {},
      cardTextContent2: {}
    }
  },
  components: { Card }
}
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: Roboto, Avenir, Helvetica, Arial, sans-serif;
}

.p-text {
  color: #2D2D2D;
}

.h-mb-24 {
  margin-bottom: 24px;
}

.h-m-24 {
  margin: 24px;
}

#app {
  display: flex;
  flex-direction: row;
  flex-wrap:wrap;
  padding: 60px 50px;
  & > div {
    margin: 15px;
  }
}
</style>
