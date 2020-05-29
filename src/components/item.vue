<template>
  <div class="item-wrapper">
    <div
      :class="`item ${selected ? 'active' : ''} ${!item.selectable ? 'notSelectable' : ''}`"
      :style="selected ? `border-color: ${colorSchema}` : ''"
      @click="$emit('clickTrigger', item)"
    >
      <img
        :src="item.backgroundImage"
        class="item-image"
      >
      <div :class="`isSelectedBox ${selected ? 'active' : ''}`">
        <transition-group
          name="fade"
          mode="out-in"
        >
          <svg
            key="checked"
            v-if="selected"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <rect
              width="24"
              height="24"
              rx="12"
              :fill="colorSchema"
            />
            <path
              d="M8 12.5L10.6667 15L16 9"
              stroke="white"
              stroke-width="1.5"
            />
          </svg>

          <svg
            key="unchecked"
            v-else
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <rect
              x="0.5"
              y="0.5"
              width="23"
              height="23"
              rx="11.5"
              fill="white"
              stroke="#97999B"
            />
          </svg>
        </transition-group>
      </div>
    </div>
    <div class="title">
      {{item.title}}

    </div>
  </div>
</template>

<script>
export default {
  props: {
    item: {
      required: true,
      type: Object
    },
    selected: {
      required: true,
      type: Boolean
    },
    colorSchema: {
      required: true,
      type: String
    }
  }
}
</script>

<style lang="scss" scoped>
.item-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.fade-enter-active,
.fade-leave-active {
  opacity: 1;
  transition: 0.4s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
.title {
  width: 180px;
  text-align: center;
  margin-right: 0;
}
.item {
  height: 180px;
  width: 180px;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  margin: 16px;
  position: relative;
  background-size: cover;
  background: #ffffff;
  border: 1px solid #dddfe1;
  box-sizing: border-box;
  border-radius: 4px;
  overflow: hidden;
  .item-image {
    max-width: 95%;
    max-height: 95%;
    object-fit: cover;
    padding: 10px;
    -webkit-touch-callout: none;
    -webkit-user-select: none;
    -khtml-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }

  &.active,
  &:hover {
    border: 1px solid #8b8b8b;
    box-sizing: border-box;
    border-radius: 4px;
    transition: 0.4s ease-in-out;
  }

  &.notSelectable {
    opacity: 0.6;
    -webkit-filter: grayscale(100%); /* Safari 6.0 - 9.0 */
    filter: grayscale(100%);
  }
  .isSelectedBox {
    border-radius: 5px;
    position: absolute;
    top: 16px;
    left: 16px;
    user-select: none;
    svg {
      position: absolute;
    }
  }
}
</style>
