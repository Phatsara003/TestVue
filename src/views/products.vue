<template>
    <div>
        <h1>Customer List</h1>
        <b-table striped hover  :items="customers" 
                                :fields="fields" 
                                :per-page="pagesize"
                                :current-page="pageindex"></b-table>
         <b-pagination size="md" :total-rows="products.length" v-model="pageindex" :per-page="pagesize"></b-pagination>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    
     name: 'customers',
 
  data(){
      return{
          message:'ProjectFinal',
          customers:[],
          pagesize: 10,
          pageindex: 1,
          fields:[             
              {
                  key:'id',
                  sortable : true

              },
              {
                  key:'title',
                  sortable : true

              },
              {
                  key:'price',
                  sortable : true,
                  variant:'warning'

              },
              
              ],
      }
  },
  mounted(){
      var instace = this
        axios
      .get('https://polar-refuge-98880.herokuapp.com/api/customers')
      .then(function(response){
          console.log(response.data)
          instace.customers = response.data.data
      })
  }
}

</script>
