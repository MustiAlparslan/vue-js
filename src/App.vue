

<template>
    <div class="container">
        <div class="row ">
          <div class="col-3 p-4  mb-2 m-1 text-white  bg-primary" @click="greet(item.name)" v-b-modal.modal-1 v-for="(item, key) in this.info" :key="key">
            {{ item.name }}
          </div>
        </div>

        <b-modal id="modal-1" title="BootstrapVue">
            <p class="my-4">{{this.productName}}</p>
        </b-modal>
    </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  data() {
        return {
            modalShow: false,
            info: [],
            productName: String, 
            config: {
                headers: {
                    "accept-language": "TR"
                }
            }
        };
    },
    methods: {
        greet(name) {
            this.productName = name
        }
        },
    mounted() {
        axios.get("http://89.252.140.57:8080/category/?pageNumber=0&pageSize=38", this.config)
            .then(data => (this.info = data.data.data))
            .catch(err => console.log(err))
    }
}
</script>

<style>
</style>
