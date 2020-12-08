<template>
  <div
    class="card"
    :class="[cardSize, {'thumbnailTop': thumbnailTop, 'cardLoader': showLoader, 'noCover': hideCover, 'noFooter': !hasFooterSlot}]"
    @click="$emit('clickhendle', cardTextContent)"
    tabindex="0" role="button" aria-pressed="false"
  >
    <div v-if="showLoader" class="loader" :class="{'noAvatar': hideAvatar}"></div>
    <card-thumbnail
      v-if="thumbnailTop"
      thumbnailPositionTop
      :hideAvatar="hideAvatar"
      :cardTextContent="cardTextContent"
    />
    
    <img v-if="!hideCover" class="cardCaver" :src="cardTextContent.url" />
    
    <div class="cardContent">
      <card-thumbnail
        v-if="!thumbnailTop"
        :hideAvatar="hideAvatar"
        :cardTextContent="cardTextContent"
      />

      <div v-if="hasBodySlot" class="cardBody">
        <slot name="body"></slot>
      </div>
    </div>

    <div v-if="hasFooterSlot" class="cardFooter">
      <slot name="footer"></slot>
    </div>
  </div>
</template>

<script>
import CardThumbnail from './CardThumbnail'

export default {
  name: 'Card',
  props: {
    size: {
      type: String,
      default: ""
    },
    thumbnailTop: {
      type: Boolean,
      default: false
    },
    hideCover: {
      type: Boolean,
      default: false
    },
    hideAvatar: {
      type: Boolean,
      default: false
    },
    cardTextContent: {
      type: Object,
      default:() => {}
    }
  },
  computed: {
    showLoader () {
      return (Object.keys(this.cardTextContent).length === 0)
    },
    hasBodySlot () {
      return !!this.$slots.body
    },
    hasFooterSlot () {
      return !!this.$slots.footer
    },
    cardSize () {
      let cardSize = ''
      switch(this.size) {
        case 'l':
        case 'L':
          cardSize = 'large'
          break
        case 'xl':
          case 'XL':
            cardSize = 'xLarge'
            break
        default:
      }
      return cardSize
    }
  },
  components: { CardThumbnail }
}
</script>

<style lang="scss" scoped>
$primary: #2D2D2D;
$secondary: #6E6E6E;
$bg: #fff;

* {
  color: $primary;
}

.card { 
  width: 327px;
  overflow: hidden;
  display: grid;
  text-align: start;
  background-color: $bg;
  border: 1px solid #{$primary} + 33;
  border-radius: 4px;
  cursor: pointer;
  position: relative;
  grid-template-rows: 200px auto 68px;
  &.noFooter {
    grid-template-rows: 200px auto;
  }
  &:focus {
    outline-color: #2F2A8D;
  }
  &:active {
    background-color: #{$primary} + 0A;
  }
  &.noCover {
    grid-template-rows: auto 68px;
    &.noFooter {
      grid-template-rows: auto;
    }
  }
  &.cardLoader {
    pointer-events: none;
    border: none;
  }
  &.thumbnailTop{
    grid-template-rows: 108px 200px auto 68px;
    &.noFooter {
      grid-template-rows: 108px 200px auto;
    }
  }
  &.large {
    width: 544px;
  }
  &.xLarge {
    width: 541px;
    grid-template-rows: 331px auto 68px;
    &.noFooter {
      grid-template-rows: 331px auto;
    }
    &.thumbnailTop {
      grid-template-rows: 108px 331px auto 68px;
      &.noFooter {
        grid-template-rows: 108px 331px auto;
      }
    }
    &.noCover {
      grid-template-rows: auto 68px;
      &.noFooter {
        grid-template-rows: auto;
      }
    }
    .cardCaver {
      height: 331px;
    }
  }
}
.loader {
  width: 100%;
  height: 100%;
  position: absolute;
  background: $bg url(~@/assets/bigLoader.svg) 0px 0px/auto 472px no-repeat;
  &.noAvatar{
    background: $bg url(~@/assets/loader.svg) 0px 0px/ 327px 395px no-repeat;
  }
}
.cardCaver {
  width: 100%;
  height: 200px;
  object-fit: cover;
}

.cardContent {
  padding: 24px;
}
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
    font-size: 20px;
    font-weight: bold;
  }
  p {
    font-size: 14px;
    font-weight: medium;
    color: $secondary;
  }
}
.cardFooter {
  height: 68px;
  padding: 24px;
  line-height: 20px;
  border-top: 1px solid #{$primary} + 33;
  color: $secondary;
}
</style>
