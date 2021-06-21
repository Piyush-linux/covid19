<template>
    <select class="form-select form-select-lg mb-3" name="country" id="" v-model="selected" @change="selection" aria-label=".form-select-lg example">
        <!-- <option selected>Select a country ...</option> -->
        <option v-for="(con , id) in country" :key="id"> {{ con.location }} </option>
    </select>
</template>
<script>
export default {
    name: 'Select',
    props: ['country'],
    data(){
      return{
        selected:''
      }
    },
    methods:{
      selection(){
        let selectedCountry = this.country.find((con)=> con.location == this.selected )
        // this.country.map((itm)=>console.log(itm))
        this.$emit('selectEmit',selectedCountry)
      }
    }
}
</script>
