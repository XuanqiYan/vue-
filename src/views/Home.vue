<template>
    <div class="home">
        <button @click='verify' >验证滑块</button>
        <Vcode 
            :show="isShow"
            @fail='onfail' 
            successText='验证成功' 
            failText='验证失败'
            :imgs='[Img1,Img2]'
            @success="onSuccess" />
    </div>
</template>

<script>
import Vcode from "vue-puzzle-vcode";

import Img1 from '@/assets/3.jpeg';
import Img2 from '@/assets/5.jpeg';

export default {
    data() {
        return {
            isShow: false, // 验证码模态框是否出现,
            Img1,
            Img2,
        };
    },
    components: {
        Vcode,
    },
    methods: {
        verify(){
            this.isShow = true
        },    
        // 用户通过了验证
        onSuccess(msg) {
            console.log(msg)
            this.isShow = false; // 通过验证后，需要手动隐藏模态框
        },
        // 用户未通过验证
        onfail(){
            console.log('fail')
        }
    },
};
</script>
