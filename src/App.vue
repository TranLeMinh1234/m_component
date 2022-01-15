<template>
  <div id="app">
    <div style="position: relative;width: 300px; margin-left:20px;margin-top: 20px">
      <validateObserve ref="observe">
        <combobox 
          query="remote"
          v-model="dataCheck"
          displayField="displayField"
          valueField="valueField"
          :dataStore="dataStore"
          rules="required"
        />
        <span>{{dataCheck}}</span>
        <combobox 
          query="remote"
          v-model="dataCheck1"
          displayField="displayField"
          valueField="valueField"
          :dataStore="dataStore"
          rules="required"
        />
        <span>{{dataCheck1}}</span>
      </validateObserve>
      <button @click="minh()">minh</button>
    </div>
  </div>
</template>

<script>
// eslint-disable-next-line no-unused-vars
import combobox from './components/combobox.vue';
import validateObserve from './components/validateObserve.vue';

export default {
  name: 'App',
  components: {
    combobox,
    validateObserve
  },
  methods:{
    minh()
    {
      let me = this;
      me.$refs.observe.validateComponent();
    }
  },
  data(){
    return {
      dataCheck: 'asdasd',
      dataCheck1: 'asdasd',
      dataStore: [
                {
                    displayField: 'Hà Nội',
                    valueField: '001'
                },{
                    displayField: 'Cà Mau',
                    valueField: '002'
                },{
                    displayField: 'Cần Thơ',
                    valueField: '003'
                },{
                    displayField: 'Kiên Giang',
                    valueField: '004'
                },{
                    displayField: 'Bắc Ninh',
                    valueField: '005'
                }
            ],
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
