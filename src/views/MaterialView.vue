<script>

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
							<tr class="material__row material__row--color-1">
									<td>12345</td>
									<td>gaze</td>
									<td><a v-on:click="Search"><i class="bx bx-copy bx-md"></i></a></td>
							</tr>
							<tr class="material__row material__row--color-2">
									<td>67890</td>
									<td>curativo</td>
									<td><i class="bx bx-copy bx-md"></i></td>
							</tr>
							<tr class="material__row material__row--color-1">
									<td>11123</td>
									<td>máscara</td>
									<td><i class="bx bx-copy bx-md"></i></td>
							</tr>
						</tbody>
					</table>
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
    border-bottom:2px solid black;
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
    text-transform: capitalize;
}

</style>