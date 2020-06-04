# Vue Select Image

Vue Select Image is a Vue.js component for selecting images.
![Vue Select Image Demo](https://raw.githubusercontent.com/cagataykula/v-select-image/master/src/assets/demo.gif)

# Installation

Use the npm package manager to install it in your project.

    npm install --save v-select-image

# Basic Usage

The most common usage is to pass a data array to the component and include it in your project.

   
	import vSelectImage from 'v-select-image'

    new Vue({
        el: '#select',
        template:'<v-select-image :items="myItems" v-model="selectedItems"/>',
        components:{vSelectImage},
        data: {
			selectedItems:[],
            myItems: [
              {
                id: 1,
                title: '',
                backgroundImage: 'https://picsum.photos/300/300?id=1',
                selectable: true
              },
              {
                id: 2,
                title: '',
                backgroundImage: 'https://picsum.photos/300/300?id=2',
                selectable: true
              },
              {
                id: 3,
                title: '',
                backgroundImage: 'https://picsum.photos/300/300?id=3',
                selectable: true
              },
              {
                id: 4,
                title: '',
                backgroundImage: 'https://picsum.photos/300/300?id=4',
                selectable: true
              },
              {
                id: 5,
                title: '',
                backgroundImage: 'https://picsum.photos/300/300?id=5',
                selectable: true
              },
              {
                id: 6,
                title: '',
                backgroundImage: 'https://picsum.photos/300/300?id=6',
                selectable: true
              }],
            selectedVal: null
        }
    })

## Parameters

You can use easily with use **\<v-select-image\>** tag.
Example:

    <v-select-image
    	class="w-650"
    	v-model="selectedItems"
    	:items="items"
    	colorSchema="#8B8B8B"
    />
    

##  Properties

You can add some parameters to customizing.
|Property|type|required  | default|
|--|--|--|--|
|items|Array|true||
|colorSchema|String|false|#8B8B8B|
|maxSelectable|String/Integer|false|-1|
|uniqueKey|String|false|id|

## Max Selection Error Handling
You can add **@maxSelectionError** prop to the **\<v-select-image\>** tag to handle maximum number of selected items.
 
 Example: 

    <v-select-image
    	class="w-650"
    	v-model="selectedItems"
    	:items="items"
    	maxSelectable="3"
    	@maxSelectionError="yourErrorFunction()"
    />

## Bugs and Improvements

If you can find a bug or design issues you can open an issue on GitHub. Don't hesitate to contribute. Your feedback is appreciated!