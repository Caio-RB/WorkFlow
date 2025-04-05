<script>
import db from "../../public/database/MaterialDB.json"
export default{
  data(){
    return{
      materials:db,
      material_search:""
    }
  },
  methods:{
    filteredList(){
      return this.materials.filter((material)=>
      material.name.toLowerCase().includes(this.material_search.toLowerCase())
    )
    }
  }
}
</script>

<template>
<div class="material">
					<span class="material__search-container">
								<i class="bx bx-search bx-md"></i>
								<input type="search" v-model="material_search" class="material__search">
					</span>
					<table class="material__table">
						<thead>
							<tr class="material__row">
									<th>código</th>
									<th>material</th>
									<th>copiar</th>
							</tr>
						</thead>
						<tbody>
							<tr class="material__row" v-for="(material, index) in filteredList()" :key="material.id"
              :class="{'material__row--color-1': index % 2 === 0, 'material__row--color-2': index % 2 !== 0}">
									<td>{{ material.code }}</td>
									<td>{{ material.name }}</td>
									<td><a v-on:click="Search"><i class="bx bx-copy bx-md"></i></a></td>
							</tr>
						</tbody>
					</table>
          <span class="material__fab"><i class="bx bx-plus bx-md"></i></span>
			  </div>
</template>

<style>
.material{
    margin-top:5vh;
    width:100vw;
    height: 72vh;
    overflow-y: scroll;
    overflow-x:hidden ;
     /* border: 2px solid yellow;  */
}

.material__table{
    width:90%;
    height:80%;
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
    list-style-type:none;
    margin: 3vh auto 0 auto;
    text-transform: uppercase;
}

.material__row{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    border-bottom: 2px solid var(--logo-color);
    align-items: center;
}
.material__row--color-1{
    background-color:var(--table-line-1);
}

.material__row--color-2{
    background-color:var(--table-line-2);
}
.material__search-container{
    display: flex;
    border: 3px solid var(--logo-color);
    background-color:var(--logo-color);
    color:var(--tertiary-color);
    border-radius: 3cqw;
    flex-direction: row;
    align-items: center;
    width: 90%;
    margin: 0 auto;
    opacity: 80%;
}
.material__search{
    flex:1;
    border:none;
    outline: none;
    background-color:var(--logo-color);
    color:var(--tertiary-color);
    text-transform: lowercase;
}
.material__fab{
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

.material__fab:hover, .material__fab:active{
    background-color:var(--active-action-color);
    border-color: var(--active-action-color);
}

/* print section*/
@media print{
  .header{
    display: none !important;
  }
  .menu__container{
    display: none !important;
  }
  .material__search-container{
    display: none !important;
  }
  #__vue-devtools-container__{
    display: none !important;
  }
  .material__fab{
    display: none !important;
  }
  .material{
    width: 100vw !important;
    height: 100vh !important;
    margin: 0;
  }
  .material__table{
    width: 100% !important;
    height: 100% !important;
  }
}
</style>