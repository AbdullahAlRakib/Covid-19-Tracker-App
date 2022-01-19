<template>
<div>
    <h3>{{text}}</h3>
</div>  
<div>
   <p>{{timestamp}} </p>
    </div>  
</template>

<script>
import moment from 'moment'
export default{
    name:'DataTitle',
    props:['text','dataDate'],
    computed:{
        timestamp:function(){
            return moment(this.dataDate).format('MMMM Do YYYY,h:mm:ss a')
        }
    }
}
</script>
