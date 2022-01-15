<template>
    <div class="validateObserve">
        <slot></slot>
    </div>
</template>

<script>
export default {
    name: 'validateObserve',
    methods:{

        //validate tất cả compoent con
        validateComponent()
        {
            let me = this;
            let errorList = [];
            // lấy các component con để validate
            let validateComponentArr = me.$children;
            // duyệt từng component với thông tin validate bắn ra bởi hàm InfoValidate()
            for(let i = 0;i < validateComponentArr.length;i++)
            {
                // lấy thông tin validate từng component
                let componentValidate = validateComponentArr[i];
                let inforValidate = componentValidate.infoValidate();
                // kiểm tra tính hợp lệ
                let errorsComponet = me.validateRules(inforValidate);

                if(errorsComponet && errorsComponet.length > 0)
                {
                    //bật cờ invalid cho component
                    componentValidate.$data.isValid = false;

                    errorList.concat(inforValidate);
                }
            }

            //focus vào input đầu tiên bị lỗi


            return errorList.length === 0;
        },

        // thực hiển kiểm tra theo rules
        validateRules(infoValidate)
        {
            let me = this;
            infoValidate.errorsComponet = [];
            let rules = infoValidate.rules.split("|");
            for(let i = 0; i < rules.length;i++)
            {
                let isValid = true;
                switch(rules[i])
                {
                    case "required":
                        isValid = me.required(infoValidate.valueValidate);
                        break;
                    default:
                        break;    

                }

                if(!isValid)
                    infoValidate.errorsComponet.push(rules[i]);
            }

            return infoValidate.errorsComponet;
        },

        required(valueValidate){
            return valueValidate !== null && valueValidate !== undefined && valueValidate !== "";
        },
    },
    data(){
        return {

        }
    }
}
</script>

<style scoped>
    
</style>