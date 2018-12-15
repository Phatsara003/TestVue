<template>
    <div>
        <h1>Product List</h1>
        <b-table striped hover  :items="products" 
                                :fields="fields" 
                                :per-page="pagesize"
                                :current-page="pageindex"></b-table>
         <b-pagination size="md" :total-rows="products.length" v-model="pageindex" :per-page="pagesize"></b-pagination>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    
     name: 'products',
 
  data(){
      return{
          message:'ProjectFinal',
          products:[],
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
      .get('https://intense-ravine-10871.herokuapp.com/api/products')
      .then(function(response){
          console.log(response.data)
          instace.products = response.data.data
      })
  }
}

</script>
