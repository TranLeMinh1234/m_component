<template>
    <div class="dropdown" v-show="onOffShow">
        <div v-for="(item,index) in valueSearch? dataFilter:dataStore" :key="index">
            <div class="dropdown-item" @click="selectItem(item,index)" >{{item[displayField]}}</div>
        </div>
    </div>
</template>

<script>
// eslint-disable-next-line no-unused-vars
export default {
    name: 'dropdown',
    props: {
        data: {
            type: Array,
            default: function(){return [];}
        },
        valueSearch: {
            type: String,
            default: '',
        },
        query: {
            type: String,
            default: ''
        },
        onOffShow: {
            type: Boolean,
            default: false
        },
        displayField: {
            type: String,
            default:''
        }
    },
    watch: {
        valueSearch: function()
        {
            let me = this; 
            me.dataFilter = me.dataStore.filter((ele)=>{return ele[me.displayField].toLowerCase().includes(me.valueSearch.toLowerCase(),0)})
        }
    },
    created(){
    },
    mounted(){
        let me = this;
        me.setUpEvent();
    },
    methods:{
        setUpEvent()
        {
            let me = this;
            
            //scroll event
            let dropdown = me.$el;
            if(me.query == "remote")
            {
                dropdown.onscroll = function(){
                if(dropdown.scrollTop + dropdown.clientHeight === dropdown.scrollHeight)
                    me.dataStore = me.dataStore.concat([{
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
                    }]);
                };
            }
        },
        selectItem(item,index)
        {
            let me = this;
            me.$emit('change',item,index);
        },
    },
    data(){
        return {
            dataStore: this.data,
            dataFilter: [],
        }
    },
}
</script>

<style scope>
@import url('../assets/css/dropdown.css');
@import url('../assets/css/main.css');
</style>