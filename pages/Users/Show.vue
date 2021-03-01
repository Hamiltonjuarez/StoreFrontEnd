<template>
    
</template>
<script>
export default {
    data(){
        return{
            results:[],
        }
    },
    mounted() {
        this.retreiveUser()
        console.log('requesting data')
    },
    methods:
    {
      async retreiveUser() {
        const ip = await this.$axios.$get('http://127.0.0.1:8000/api/users/'+this.$route.query.userId)
        this.results = ip     
      },
      showUser(id){
        console.log(id)
      }
    },
}
</script>