<template>
  <div class="d-flex flex-column justify-center align-center">
    <div class="d-flex flex-row justify-center align-center">

      <v-select-image
        class="w-650"
        v-model="selectedItems"
        :items="items"
        :colorSchema="colorSchema"
        uniqueKey="key"
        :maxSelectable="maxSelectable"
        @maxSelectionError="maxSelected()"
      />
    </div>
    <div class="">

    <div class="d-flex flex-row w-650 mt-25">
      <span style="font-size: 18px">Max Selectable: </span>
      <input
        style="width: 30px; margin-left: 5px; margin-right: 5px; font-size: 14px"
        type="number"
        v-model="maxSelectable"
      >
      <span style="font-size: 15px; font-color: gray"> (-1 is unlimited)</span>
    </div>
    <div class="d-flex flex-row w-650 mt-25">
      <span style="font-size: 18px">Color Schema: </span>
      <input
        style="width: 60px; margin-left: 5px; margin-right: 5px; font-size: 14px"
        type="text"
        v-model="colorSchema"
      >
      <span style="font-size: 15px; font-color: gray"></span>
    </div>
    </div>

    <div class="mt-20 d-flex flex-column w-650">
      <pre
        style="padding-left: 30px;"
        :style="`border-left-color: ${colorSchema}`"
      ><code><strong>selectedItems</strong>: {{selectedItems}}</code></pre>
    </div>
    <div class="mt-20 d-flex flex-column w-650">
      <pre style="padding-left: 30px;"><code><strong>items</strong>: {{items}}</code></pre>
    </div>
  </div>
</template>

<script>
import VSelectImage from './VueSelectImage'

export default {
  name: 'App',
  components: { VSelectImage },
  methods: {
    maxSelected () {
      alert('You cant select more than ' + this.maxSelectable)
    }
  },
  data () {
    return {
      maxSelectable: -1,
      selectedItems: [],
      items: [
        {
          key: 1,
          title: '',
          backgroundImage: 'https://picsum.photos/300/300?id=1',
          selectable: true
        },
        {
          key: 2,
          title: '',
          backgroundImage: 'https://picsum.photos/300/300?id=2',
          selectable: true
        },
        {
          key: 3,
          title: '',
          backgroundImage: 'https://picsum.photos/300/300?id=3',
          selectable: true
        },
        {
          key: 4,
          title: '',
          backgroundImage: 'https://picsum.photos/300/300?id=4',
          selectable: true
        },
        {
          key: 5,
          title: '',
          backgroundImage: 'https://picsum.photos/300/300?id=5',
          selectable: true
        },
        {
          key: 6,
          title: '',
          backgroundImage: 'https://picsum.photos/300/300?id=6',
          selectable: true
        }
      ],
      colorSchema: '#8B8B8B'
    }
  },
  watch: {
    maxSelectable (newVal, oldVal) {
      if (newVal < this.selectedItems.length) {
        this.maxSelectable = oldVal
      }
      if (this.items.length < newVal) {
        this.maxSelectable = oldVal
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.d-flex {
  display: flex;
}

.flex-row {
  flex-direction: row;
}

.flex-column {
  flex-direction: column;
}

.justify-center {
  justify-content: center;
}

.align-center {
  align-items: center;
}
.w-650 {
  max-width: 650px;
}

.mt-20 {
  margin-top: 20px;
}

.mt-25 {
  margin-top: 20px;
}

pre {
  counter-reset: line-numbering;
  background: #2c3e50;
  padding: 12px 0px 14px 0;
  width: 600px;
  color: #ecf0f1;
  line-height: 100%;
}

pre code .line::before {
  content: counter(line-numbering);
  counter-increment: line-numbering;
  padding-right: 1em;
  /* space after numbers */
  padding-left: 8px;
  width: 1.5em;
  text-align: right;
  opacity: 0.5;
  color: white;
}
</style>
