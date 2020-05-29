# Vue Select Image

Its is a Vue.js component for selecting images. 
![Vue Select Image Demo](https://raw.githubusercontent.com/cagataykula/v-select-image/master/src/assets/demo.gif)

# Installation

Firstly you can install with only npm for now

    npm install --save v-select-image
After installation you have to import component wherever want you to use.

    import VueSelectImage from 'v-select-image'
After that you have to register it as a component in your script

    <script>
	    components: { VueSelectImage }
    </script>


## Usage

You can use easily with use **\<v-select-image\>** tag.
Example:

    <v-select-image
    	class="w-650"
    	v-model="selectedItems"
    	:items="items"
    	colorSchema="##8B8B8B"
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
You can add **@maxSelectionError** prop to the **\<v-select-image\>** tag.
 
 Example: 

    <v-select-image
    	class="w-650"
    	v-model="selectedItems"
    	:items="items"
    	maxSelectable="3"
    	@maxSelectionError="yourErrorFunction()"
    />

## Bugs and Improvements

If you can find a bug or design issue you can open an issue on GitHub or you can fix directly. Dont hesitate to contribute