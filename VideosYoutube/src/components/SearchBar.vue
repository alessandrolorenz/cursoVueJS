<template>
  <div>
    <input type="text" @input="onInput"/>
    <button type="button" @click="onClick" >Search</button>
  </div>  
</template>

<script>
export default {
  name: 'SearchBar',
    data() {
       return { searchVideos: ''}
    },
  methods: {
    onInput: function(event) {  
      // this.$emit('termChange', event.target.value)
      this.searchVideos = event.target.value
      },
    onClick: function() {
      console.log()
      this.$emit('termChange', this.searchVideos)
    }

  },

}
</script>

<style lang="scss" scoped>
  div {
    text-align: center;
    margin: 20px;

    input {
      width: 75%;
    }


  }

</style>>
