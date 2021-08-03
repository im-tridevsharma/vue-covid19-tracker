<template>
    <div class="p-3 text-center mb-3">
        <h1 class="text-3xl">{{ title }}</h1>
        <p class="mt-3 text-grey-darkest">{{ formatedDateTime }}</p>
    </div>
</template>

<script>
import moment from 'moment'

export default {
    name: "Title",
    props:['title', 'datetime'],
    computed:{
        formatedDateTime(){
            return moment(this.datetime).format('MMMM Do YYYY, h:mm:ss a')
        }
    }
}
</script>
