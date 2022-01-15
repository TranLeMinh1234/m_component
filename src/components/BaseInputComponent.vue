<template>
    <div class="base-intput-component"></div>
</template>

<script>
export default {
    name: 'BaseInputComponent',
    mounted(){
        let me = this;
        me.infoValidate = me.validateInfoSelf();

    },
    methods:
    {
        // hàm trả ra thông tin vần validate của component, override lại ở compo con
        // sử dụng với trường hợp cần thông tin để validate nhiều compo một lục
        validateInfoSelf()
        {
            return {}; 
        },
        
        //hàm tự validate lại ngay khi thay đổi trên component
        validateSelf()
        {
            let me = this;
            
        }
    },
    data()
    {
        return {
            isValid: true,
        };
    }

}
</script>

<style>
    
</style>