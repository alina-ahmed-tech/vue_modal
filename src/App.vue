<template>
  <h1>{{ title }}</h1> 
  <teleport to=".modals" v-if="showModal">
    <Modal text="Get cookies half price" :header="header" theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">Sign up now.</a>
        <a href="#">More info.</a>
      </template>
      <h2>This is a header to show slots</h2> 
      <p>This is some text to show slots blah blah blah</p>
    </Modal>  
  </teleport>
  <button class="nicebut" @click.shift="toggleModal"> Open Modal - you need to hold shift and click </button>
  <input type="text" ref="userName">
  <button @click="handleClicking">Click Me!</button>
</template>

<script>
import Modal from './components/Modal.vue' //in order to use another component, there are 2 steps: import it and list it in the root object.
//Then just put the modal tag "<Modal />" where you want the code from the modal component file to be 


export default {  //the root component object. List components here you want to use e.g. Modal component
  name: 'App',  
  components: { Modal },
  data() {
    return {
      title: 'First Vue App',
      header: 'Sign up for the giveaway!',
      showModal: false 
    }
  },
  methods: {
    handleClicking() {
      console.log(this.$refs.userName)
    },
    toggleModal() {
      this.showModal = !this.showModal
    }
  }
  }

</script>

<style> 
#app, .modals   {                  
  font-family: Avenir, Helvetica, Arial, sans-serif; 
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid cornflowerblue;
  display: inline-block;
  padding-bottom: 10px;
}

.nicebut {
  color:red;
  justify-content: center;
  font-size: large;
}
</style>
