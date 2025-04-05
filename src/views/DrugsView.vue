<script>
import db from "../../public/database/DrugsDB.json";
export default{
  data(){
    return{
      drugs:db,
      drugs_search:"",
      drugs_button:true
    }
  },
  methods:{
    filteredList(){
      return this.drugs.filter((drug)=>
        drug.name.toLowerCase().includes(this.drugs_search.toLowerCase())
      )
    }
  }
}
</script>
<template>
<div class="drugs">
					<span class="drugs__search-container">
								<i class="bx bx-search bx-md"></i>
								<input type="search" v-model="drugs_search" class="drugs__search">
					</span>
					<table class="drugs__table">
						<thead>
							<tr class="drugs__row">
									<th>código</th>
									<th>drogas</th>
									<th>copiar</th>
							</tr>
						</thead>
						<tbody>
							<tr class="drugs__row" v-for="(drug,index) in filteredList()" :key="drug.id"
              :class="{'drugs__row--color-1':index % 2 === 0, 'drugs__row--color-2':index % 2 !== 0}">
									<td>{{ drug.code }}</td>
									<td>{{ drug.name }}</td>
									<td><a v-on:click="Search"><i class="bx bx-copy bx-md"></i></a></td>
							</tr>
						</tbody>
					</table>
          <div class="drugs__fab">
              <span class="drugs__button" v-show="drugs_button"><i class="bx bx-file bx-md"></i></span>
              <span class="drugs__button" v-show="drugs_button"><i class="bx bx-printer bx-md"></i></span>
              <span class="drugs__button"><i class="bx bx-plus bx-md"></i></span>
          </div>
			  </div>
</template>
<style>
.drugs{
    margin-top:5vh;
    width:100vw;
    height: 72vh;
    overflow-y: scroll;
    overflow-x:hidden ;
     /* border: 2px solid yellow;  */
}

.drugs__table{
    width:90%;
    height:80%;
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
    list-style-type:none;
    margin: 3vh auto 0 auto;
    text-transform: uppercase;
}

.drugs__row{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    border-bottom: 2px solid var(--quaternary-color);
    align-items: center;
}
.drugs__row--color-1{
    background-color:var(--table-line-1);
}

.drugs__row--color-2{
    background-color:var(--table-line-2);
}
.drugs__search-container{
    display: flex;
    border: 3px solid var(--quaternary-color);
    background-color:var(--quaternary-color);
    color:var(--tertiary-color);
    border-radius: 3cqw;
    flex-direction: row;
    align-items: center;
    width: 90%;
    margin: 0 auto;
    opacity: 80%;
}
.drugs__search{
    flex:1;
    border:none;
    outline: none;
    background-color:var(--quaternary-color);
    color:var(--tertiary-color);
    text-transform: lowercase;
}
.drugs__fab{
  display:flex;
  flex-direction: column;
  justify-content:space-between;
  align-items: center;
  position:absolute;
  right: 1rem;
  height: 30vh;
  bottom: 20vh;
}
 .btn{
    border:2px solid var(--action-color);
    border-radius: 100%;
    height: 3rem;
    width: 3rem;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    background-color: var(--action-color);
    color:var(--tertiary-color);
    z-index: 3;
    position:absolute;
    right: 0;
    bottom:20vh;
    box-shadow: -3px 10px 11px 0px rgba(0,0,0,0.75);
    -webkit-box-shadow: -3px 10px 11px 0px rgba(0,0,0,0.75);
    -moz-box-shadow: -3px 10px 11px 0px rgba(0,0,0,0.75);
     margin-right: 5vw;
}
.drugs__button{
    border:2px solid var(--action-color);
    border-radius: 100%;
    height: 3rem;
    width: 3rem;
    background-color: var(--action-color);
    color:var(--tertiary-color);
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    box-shadow: -3px 10px 11px 0px rgba(0,0,0,0.75);
    -webkit-box-shadow: -3px 10px 11px 0px rgba(0,0,0,0.75);
    -moz-box-shadow: -3px 10px 11px 0px rgba(0,0,0,0.75);
}
.drugs__button:hover, .drugs__button:active{
    background-color:var(--active-action-color);
    border-color: var(--active-action-color);
}
</style>