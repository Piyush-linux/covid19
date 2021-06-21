<template>
    <div class="container-lg text-center py-5">
        <!-- header -->
        <Header />
        <!-- title -->
        <Country :title="title" />
        <!-- cases -->
          <Cases :stats="stats"/>
        <!-- select -->
        <Select :country="country" @selectEmit="countrySelect"/>
    </div>
</template>
<script>
import Header from './components/Header'
import Country from './components/Country'
import Cases from './components/Cases'
import Select from './components/Select'
export default {
    name: 'App',
    components: {
        Header,
        Country,
        Select,
        Cases
    },
    data() {
        return {
            url: 'https://www.trackcorona.live/api/countries',
            title: '',
            country: [],
            stats: {}
        }
    },
    methods: {
        async fetchCovid() {
            return await (await fetch(this.url)).json()
        },
        countrySelect(con){
          this.title = con.location
          this.stats = con
          console.log(con)
        }
    },
    async created() {
        let data = (await this.fetchCovid()).data
        let india = {};
        data.map((con)=> {
            if (con.country_code == 'in') {
                india = con
            }
             })
        // title
        this.title = india.location
        // country
        this.country = data
        // data.map((con) => this.country.push(con.location))
        // stats
        this.stats = india
    }
}
</script>