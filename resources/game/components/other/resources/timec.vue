<template>
    <div class="d-inline-block" title="Tiempo" v-if="cant>0||visible||disabled">
        <img :src="require('Img/icon/icon_time.png')" :class="disabled&&cant==0 ? 'opacity-5' : ''"> {{$sectotime(cant)}}
    </div>
</template>

<script>
export default {
    name:'timec',
    props:{
        cant:Number,
        visible:{
            type:Boolean,
            default:false
        },
        disabled:{
            type:Boolean,
            default:false
        }
    }
}
</script>
