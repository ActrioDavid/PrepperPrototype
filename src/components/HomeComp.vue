<template>
<button @click="mydebug" type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#categoryModal" >
  Öffne Lebensmittelkategorien
</button>

<!--Modal Kategorie-->
<div class="modal" tabindex="-1" id="categoryModal">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title">Kategorien</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        <p>Bitte wähle eine Unterkategorie aus</p>
        <hr>
        
        <div v-for="item in OverviewRef" v-bind:key="item">
            <button type="button" class="btn btn-primary mb-1" data-bs-toggle="modal" data-bs-target="#subcategoryModal" data-bs-dismiss="#categoryModal" @click="categoryRef=item">
                {{item.name}}
            </button>
        </div>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
      </div>
    </div>
  </div>
</div>

<!--Modal Unterkategorie-->
<div class="modal" tabindex="-1" id="subcategoryModal">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title">Unterkategorien</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        <p>Bitte wähle eine Kategorie aus</p>
        <hr>
        <div v-for="item in categoryRef.subcategories" :key="item">
            <button type="button" class="btn btn-primary mb-1" data-bs-toggle="modal" data-bs-target="#groceryViewModal" data-bs-dismiss="#subcategoryModal" @click="subcategorieRef = item">
                {{item.name}}
            </button>
        </div>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
      </div>
    </div>
  </div>
</div>

<!--Modal Lebensmittelanzeige-->
<div class="modal" tabindex="-1" id="groceryViewModal">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title">{{subcategorieRef.name}}</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        <h6>Lebensmittelformular:</h6>
        <div v-if="subcategorieRef.isText">
            <p>{{subcategorieRef.text}}</p>
        </div>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
      </div>
    </div>
  </div>
</div>
</template>

<!--script is running OnCreate-->
<script setup>
import {ref} from 'vue';

const OverviewRef = ref([
    {
        index : 0,
        name : "Dosen",
        subcategories: [
            {
                name:"Dosentomaten",
                isText:true,
                text:"Kaufland Dosentomaten."
            },
            {
                name:"Sauerkraut eingelegt",
                isText:false,
                text:""
            }
        ]
    },
    {
        index : 1,
        name : "Gemuese",
        subcategories: [
            {
                name:"Kartoffeln",
                isText:false,
                text:""
            },
            {
                name:"Blattsalat",
                isText:true,
                text:"Gute Demeterkartoffeln, anthroposophisch hergestellt."
            }
        ]
    },
        {
        index : 2,
        name : "Brot",
        subcategories: [
            
        ]
    }
]);

const categoryRef = ref(
{
        index : -1,
        name : "",
        subcategories: [
            {
                name:"",
                isText:false,
                text:""
            }        ]
});

const subcategorieRef = ref(
    {
        name:"",
        isText:false,
        text:""
    }
);
</script>

<style scoped>

</style>