<template>
  <h1>{{title}}</h1>
  <div v-if="showModal">
    <!-- <Modal :header="header" :text="text" theme="sale" @close="toggleModal"/> -->
    <Modal theme="" @close="toggleModal">
        <h1>ninja giveaway</h1>
        <p>123456789</p>
        <template v-slot:links>
          <a href="#">sig</a>
          <a href="#">mor</a>
        </template>
    </Modal>
  </div>
  <div v-if="showModalTwo">
    <Modal theme="" @close="toggleModalTwo">
        <h1>n666</h1>
        <p>123456789</p>
    </Modal>
  </div>
  <br>
  <button @click="toggleModal">open modal</button>
  <button @click="toggleModalTwo">open second modal</button>
  <!-- <input type="text" ref="name"> -->
  <!-- <button @click="handleClick">click me</button> -->
</template>

<script>
import Modal from './components/Modal.vue'
export default {
  name: 'App',
  components: {Modal},
  data(){
    return{
      title: 'my first vue app',
      header: "1234568789",
      text: "123456",
      showModal: false,
      showModalTwo: false
    }
  },
  methods:{
    // handleClick(){
    //   console.log(this.$refs.name)
    //   this.$refs.name.classList.add('active')
    //   this.$refs.name.focus()
    // }
    toggleModal(){
      this.showModal = !this.showModal
    },
    toggleModalTwo(){
      this.showModalTwo = !this.showModalTwo
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
