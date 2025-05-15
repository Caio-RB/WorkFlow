<script>
import db from "../../public/database/DrugsDB.json";
export default{
  data(){
    return{
      drugs:db,
      drugs_search:"",
      drugs_filter:db,
      drugs_request_checkbox:[],
      drugs_quantities:{}
    }
  },
  methods:{
    search(){
        this.drugs_filter = this.drugs.filter(drugs=>{
            return drugs.name.toLowerCase().includes(this.drugs_search.toLowerCase())
        })
    },
    generatePdf(){
        const form = document.getElementsByClassName("drugs__request-details")[0];
        window.html2pdf(form);
    }
  }
}
</script>

<template>
    <div class="drugs">
        <p class="title">Solicitar medicamento</p>
        <span class="drugs__search-container">
                <i class='bx bx-search bx-md drugs__search-icon'></i>
                <input type="search" placeholder="Pesquisar" v-model="drugs_search" v-on:keyup="search()" class="drugs__search">
        </span>
        <form class="drugs__form">
            <ul class="drugs__list">
                <li v-for="(drug, index) in drugs_filter" :key="drug.id" class="drugs__list-element">
                    {{ drug.name }} 
                    
                    <input 
                        type="checkbox" 
                        v-model="drugs_request_checkbox" 
                        :value="drug" 
                        class="drugs__checkbox"
                    />
                        
                    <input
                        v-show="drugs_request_checkbox.includes(drug)"
                        type="number"
                        v-model.number="drugs_quantities[drug.id]"
                        placeholder="QTD"
                        min="0"
                        class="drugs__quantity"
                    />
                </li>
            </ul>
            <div class="drugs__generate-request">
                <input type="button" value="Solicitar" @click="generatePdf()" >
            </div>
        </form>
        <div v-show="true">
            <table class="drugs__request-details">
                <thead>
                    <tr>
                        <th>código</th>
                        <th>nome</th>
                        <th>quantidade</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(checkbox) in drugs_request_checkbox">
                        <td>{{ checkbox.code }}</td>
                        <td>{{ checkbox.name }}</td>
                        <td>{{ drugs_quantities[checkbox.id] }}</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div> 
</template>

<style scoped>
.drugs__list{
    text-transform: uppercase;
    display:flex;
    flex-direction: column;
    width: 90%;
    margin:0 auto;
    
}
.drugs__form{
    display: flex;
    margin: 0 auto;
    flex-wrap: wrap;
}
.drugs__search-container{
    width: 80%;
    border-radius: 2cqw;
    border: 3px solid var(--quaternary-color);
    display: flex;
    background-color: var(--tertiary-color);
    margin: 0 auto;
}
.drugs__search{
    width:80%;
    border-radius: 2cqw;
    flex:1;
    border:none;
    outline: none;
    text-transform: lowercase;
    background-color: var(--tertiary-color);
    color:black;
}
.drugs__search-icon{
    align-self: center;
    left: 32;
    color:var(--quaternary-color);
    margin-left: 3vw;

}
.title{
    color:var(--quaternary-color);
}
.drugs__list-element{
    display: flex;
    justify-content: space-between;
    text-align: center;
    margin:0.8vh 0;
    border:2px solid purple;
}
.drugs__generate-request{
    margin:0 auto;
}
.drugs__checkbox{
width:1.5rem;
height: 1.5rem;
}
.drugs__quantity{
    width: 20%;
}
.drugs__request-details{
    text-transform:uppercase;
    text-align:center;
    border:double;
    width:100%;
}
</style>
