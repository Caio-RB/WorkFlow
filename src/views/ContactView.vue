<script>
import db from "../../public/database/ContactDB.json"
export default{
  data(){
    return{
      modal_visibility:false,
      contact:db,
      contact_search:"",
      contact_select_section:"choice",
      contact_select_type:"all",
      contact__accordion:true,
    }
  },
  methods:{
    showModal(){
      if(this.modal_visibility == false){
        this.modal_visibility = true;
      }
      else{
        this.modal_visibility = false;
      }
    },
    hiddenModal(){
      this.modal_visibility = false;
    },
    search(){
      for (let i = 0; i < this.contact.length; i++) {
      if (this.contact[i].contact.includes(this.contact_search)) {
        console.log("encontrado");
      } else {
        console.log("não encontrado");
      }
     }
    }
  }
}
</script>
<template>
<div class="contact">
            <form>
                <div class="contact__header">
                    <span class="contact__search-container">
                        <i class='bx bx-search bx-md contact__search-icon'></i>
                        <input type="text" class="contact__search" v-model="contact_search" placeholder="pesquisar" v-on:keyup="search">
                    </span>
                    <a href="#" class="contact__filter" @click="showModal"><i class='bx bx-filter bx-lg filter__button'></i></a>
                </div>

                <div class="contact__body">
                    <ul class="contact__list">
                        <li class="contact__number" v-if="contact__accordion">
                                <div class="contact__accordion">
                                    <p class="accordion__title">{{ contact[0].contact }}: <u>{{ contact[0].number }}</u></p>
                                    <span class="accordion__chevron-border">
                                        <a class="accordion__chevron"><i class='bx bx-chevron-up bx-md chevron__button'></i></a>
                                    </span>
                                </div>
                                <div class="contact__accordion--active">
                                    <p class="accordion__paragraph">{{ contact[0].content }}</p>
                                    <a class="copy" href="#"><i class="bx bx-copy bx-md"></i></a>
                                </div>
                        </li>

                        <li class="contact__number">
                            <div class="contact__accordion">
                                <p class="accordion__title">{{ contact[1].contact }}: <u>{{ contact[1].number }}</u></p>
                                <span class="accordion__chevron-border">
                                    <a  class="accordion__chevron"><i class='bx bx-chevron-up bx-md chevron__button'></i></a>
                                </span>
                            </div>
                            <div class="contact__accordion--active">
                                <p class="accordion__paragraph">{{ contact[1].content }}</p>
                                <a class="copy" href="#"><i class="bx bx-copy bx-md"></i></a>
                            </div>
                          </li>

                          <li class="contact__number">
                            <div class="contact__accordion">
                                <p class="accordion__title">{{ contact[2].contact }}: <u>{{ contact[2].number }}</u></p>
                                <span class="accordion__chevron-border">
                                    <a  class="accordion__chevron"><i class='bx bx-chevron-up bx-md chevron__button'></i></a>
                                </span>
                            </div>
                            <div class="contact__accordion--active">
                                <p class="accordion__paragraph">{{ contact[2].content }}</p>
                                <a class="copy" href="#"><i class="bx bx-copy bx-md"></i></a>
                            </div>
                          </li>

                          <li class="contact__number">
                            <div class="contact__accordion">
                                <p class="accordion__title">{{ contact[3].contact }}: <u>{{ contact[3].number }}</u></p>
                                <span class="accordion__chevron-border">
                                    <a  class="accordion__chevron"><i class='bx bx-chevron-up bx-md chevron__button'></i></a>
                                </span>
                            </div>
                            <div class="contact__accordion--active">
                                <p class="accordion__paragraph">{{ contact[3].content }}</p>
                                <a class="copy" href="#"><i class="bx bx-copy bx-md"></i></a>
                            </div>
                          </li>
                    </ul>

                    <div class="filter__modal" id="filter-modal" v-show="modal_visibility">
                          <span class="filter__header">
                              <a class="filter__link" @click="hiddenModal">
                                  <i class="bx bx-x bx-lg filter__button--close"></i>
                              </a>
                          </span>

                          <div class="filter__body">
                                  <span class="select">
                                      <label for="category">Setor:</label>
                                      <select name="category" class="filter__select" v-model="contact_select_section">
                                          <option value="choice">Escolha</option>
                                          <option value="ti">TI</option>
                                          <option value="emergency">Emergência</option>
                                          <option value="hospitalization">Internação</option>
                                      </select>
                                  </span>
                              <span class="select">
                                  <label for="type">Tipo:</label>
                                      <select name="type" class="filter__select" v-model="contact_select_type">
                                          <option value="all">Todos</option>
                                          <option value="landline">Fixo</option>
                                          <option value="mobile">Móvel</option>
                                      </select>
                              </span>
                              <input type="button" value="Filtrar" class="filter__apply">
                          </div>
                    </div>
                </div>
            </form>
        </div>
</template>

<style scoped>
.contact{
    margin-top:5vh;
    width:100vw;
    height: 72vh;
    overflow: scroll;
    /* border: 2px solid yellow; */
}

.contact__header{
    /* border: 2px solid red; */
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    align-items: center;
}
.contact__search-container{
    width: 72%;
    border-radius: 2cqw;
    border: 3px solid var(--primary-color);
    display: flex;
    background-color: var(--tertiary-color);
}

.contact__search{
    width:80%;
    border-radius: 2cqw;
    flex:1;
    border:none;
    outline: none;
    text-transform: lowercase;
}
.contact__search-icon{
    align-self: center;
    left: 32;
    color:var(--primary-color);
    margin-left: 3vw;

}
.contact__filter{
    color:var(--primary-color);
}
.contact__list{
    display:flex;
    justify-content: flex-start;
    width: 100%;
    height: 100%;
    margin-top: 2vh;
    flex-wrap: wrap;
    flex-direction: column;
    align-items: center;
}
.contact__number{
    width: 90%;
    height: 18vh;
    display:flex;
    flex-direction: row;
    flex-wrap: wrap;
    margin-top: 2vh;
}
.contact__accordion{
    border: 2px solid var(--primary-color);
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    height:32%;
    background-color: var(--primary-color);
}
.contact__accordion--active{
    border: 2px solid var(--primary-color);
    width: 100%;
    height: 68%;
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    text-align:justify;
    font-size: 0.9em;
    align-items: center;
    display: visible;
}

.accordion__title{
    font-size: 1.4rem;
    color:var(--tertiary-color);
    font-weight: bold;
    margin-left: 2vw;
}
.accordion__paragraph{
    width: 80%;
}

.accordion__chevron{
    color:var(--tertiary-color);
}
.accordion__chevron-border{
    border:2px solid var(--tertiary-color);
    border-radius: 100%;
    display: flex;
    margin-right: 2vw;
    cursor: pointer;
    height: 2.5rem;
    width: 2.5rem;
}

.filter__modal{
    height:40vh;
    width:70vw;
    background-color: var(--tertiary-color);
    position:absolute;
    margin:0 auto;
    top:20vh;
    right: 0;
    left:0;
    margin-top:5vh;
    border-radius: 2cqw;
    border: 3px solid var(--primary-color);
    display: visible;
    overflow: hidden;
    box-shadow: -11px 0px 5px 0px rgba(0,0,0,0.75);
    -webkit-box-shadow: -11px 0px 5px 0px rgba(0,0,0,0.75);
    -moz-box-shadow: -11px 0px 5px 0px rgba(0,0,0,0.75);
}

.filter__header{
    display:flex;
    flex-direction: row;
    justify-content: flex-end;
    margin-right:6vw;
    margin-top:5vw;
    cursor:pointer;
}

.filter__modal--active{
    display: block;
}
.filter__body{
    text-transform: uppercase;
    font-weight: 500;
    display:flex;
    flex-direction: column;
    width:70%;
    margin:0 auto;
}
.filter__select{
    background-color: var(--tertiary-color);
    border: 2px solid var(--primary-color);
    border-radius: 3cqw;
    height: 6vh;
    font-size: 1.1rem;
}
.select{
    display: flex;
    flex-direction: column;
    margin-top: 2vh;
    justify-content: center;
}

.filter__apply{
    background-color: var(--primary-color);
    color:white;
    border-style: solid;
    cursor:pointer;
    margin-top:1vh;
    padding:0.3rem;
    border-radius: 3cqw;
}
.filter__apply:active{
    background-color: var(--logo-color);
}
</style>
