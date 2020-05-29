<template>
  <div class="v-select-image-items">
    <item
      v-for="item in items"
      :item="item"
      @clickTrigger="itemClick(item)"
      :key="item.id"
      :selected="isSelected(item)"
      :colorSchema="colorSchema != '' ? colorSchema : '#8B8B8B'"
      style
    />
  </div>
</template>

<script>
import item from './item'

export default {
  name: 'v-select-image',
  components: { item },
  props: {
    items: Array,
    apiUrl: String,
    successAction: Object,
    colorSchema: {
      required: false,
      type: String,
      default: '#8B8B8B'
    },
    maxSelectable: {
      required: false,
      type: [String, Number],
      default: -1
    },
    texts: {
      required: false,
      type: Object,
      default: () => {}
    },
    uniqueKey: {
      required: false,
      type: String,
      default: 'id'
    }
  },
  data () {
    return {
      selectedItems: []
    }
  },
  methods: {
    clear () {
      this.selectedItems = []
    },
    itemClick (item) {
      const maxSelectableItem = parseInt(this.maxSelectable)
      const isSelectedBefore = this.selectedItems.findIndex(selectedItem => {
        return selectedItem[this.uniqueKey] == item[this.uniqueKey]
      })
      if (item.selectable) {
        if (isSelectedBefore != -1) {
          this.selectedItems.splice(isSelectedBefore, 1)
        } else {
          // This will be use if user selected before (NOT READY YET!)
          // this.selectedItems.forEach(selectedItem => {
          //   if(maxSelectableItem != -1 && selectedItem.selectable == false) {
          //     maxSelectableItem = maxSelectableItem + 1
          //   }
          // });
          if (
            maxSelectableItem != -1 &&
            this.selectedItems.length >= maxSelectableItem
          ) {
            return this.$emit('maxSelectionFunction')
          }
          this.selectedItems.push(item)
        }
      }
      this.$emit('input', this.selectedItems)
    },
    isSelected (selected) {
      const isSelected = this.selectedItems.find(item => {
        return item[this.uniqueKey] == selected[this.uniqueKey]
      })
      return !!isSelected
    }
  },
  beforeDestroy () {
    this.clear()
  }
}
</script>

<style lang="scss">
.v-select-image-items {
  /* row justify-content-center */
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
</style>
