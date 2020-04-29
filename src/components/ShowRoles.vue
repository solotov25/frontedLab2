<template>
    <div class="container-fluid">
        <div class="list-group">
            <div v-for="r in roles" :key="r.roleName">
              {{key}}
            </div>
        </div>
    </div>
</template>

<script>
  import axios from 'axios';

  export default {
    name: "ShowRoles",
    data( ){
      return {
        roles:[]
      };
    },
    beforeCreate( ){
      const rolPath = '/principal/roles';
      axios
        .get( this.$store.state.backURL + rolPath, {params: {
                access_token: localStorage.getItem( "token" )
              }})
        .then( res => {
          if( res.status == 200 ){
              this.roles = res.data;
          }
        })
    }
  }
</script>

<style scoped>

</style>
