<template>
    <div class="mBorder">
        <Ventana1 :close='close' :titulo="$t(`buildings[${building_id}].name`)">
            <div class="gtitle box">{{$t(`buildings[${building_id}].text`)}}</div>
            <Intendencia v-if='building_id==1' :data='info'></Intendencia>
            <Academia v-else-if='building_id==2' :data='info'></Academia>
            <Deposito v-else-if='building_id==3' :data='info'></Deposito>
            <Cuartel v-else-if='building_id==4' :data='info'></Cuartel>
            <Taberna v-else-if='building_id==5' :data='info'></Taberna>
            <Reductores v-else-if='building_id>=6&&building_id<=10' :data='info'></Reductores>
            <Productores v-else-if='building_id>=11&&building_id<=15' :data='info'></Productores>
            <Puerto v-else-if='building_id==16' :data='info'></Puerto>
        </Ventana1>
        <Ventana2 titulo="Ampliar">
            <Ampliar :info='info'></Ampliar>
            <ColaUnidades v-if='building_id==4'></ColaUnidades>
        </Ventana2>
    </div>
</template>

<script>
import Ventana1 from 'Components/modal/Ventanas/Ventana1.vue'
import Ventana2 from 'Components/modal/Ventanas/Ventana2.vue'
import Ampliar from 'Components/modal/Edificios/Ampliar.vue'
import Intendencia from 'Components/modal/Edificios/Intendencia/Intendencia.vue'
import Academia from 'Components/modal/Edificios/Academia.vue'
import Deposito from 'Components/modal/Edificios/Deposito.vue'
import Reductores from 'Components/modal/Edificios/Reductores.vue'
import Productores from 'Components/modal/Edificios/Productores.vue'
import Puerto from 'Components/modal/Edificios/Puerto.vue'
import Taberna from 'Components/modal/Edificios/Taberna.vue'
import Cuartel from 'Components/modal/Edificios/Cuartel/Cuartel.vue'
import ColaUnidades from 'Components/modal/Edificios/Cuartel/ColaUnidades.vue'

export default {
    name: 'Edificios',
    props:['info','close'],
    components:{
        Ventana1,
        Ventana2,
        Ampliar,
        Intendencia,
        Academia,
        Deposito,
        Reductores,
        Productores,
        Puerto,
        Taberna,
        Cuartel,
        ColaUnidades
    },
    data(){
        return {
            building_id:0
        }
    },
    watch:{
        info(){
            this.building_id = this.info.building_id;
        }
    },
    beforeMount(){
        this.building_id = this.info.building_id;
    }
}
</script>

<style lang="scss" scoped>
    @import '~Sass/modal';
    .gtitle{
        font-weight: 400;
        text-align: justify;
    }
</style>
