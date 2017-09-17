<template>
  <div @click='submitmethod()' id="list" class="layout-padding row justify-center">
    <div style="max-height:100%; overflow-y: auto;">
      <q-list highlight id="qList" class="max-height:500px;" v-for="item in items.data" v-bind:style='{fontSize: "3.5vh", fontWeight: "bold"}'>
        <q-item>
          <q-item-side>
            <q-item-tile avatar>
              <img src="http://via.placeholder.com/350x150" />
            </q-item-tile>
          </q-item-side>
          <q-item-main>
             <q-item-tile label>{{item.email}}</q-item-tile>
             <q-item-tile sublabel>{{item.role}}</q-item-tile>
         </q-item-main>
         <q-item-side right stamp="10% match" />
        </q-item>
      </q-list>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import {
  QList,
  QListHeader,
  QItem,
  QItemSeparator,
  QItemSide,
  QItemMain,
  QItemTile,
  QChip,
  QPopover
} from 'quasar'
export default {
  components: {
    QList,
    QListHeader,
    QItem,
    QItemSeparator,
    QItemSide,
    QItemMain,
    QItemTile,
    QChip,
    QPopover
  },
  name: 'page5',
  data(){
    return {
      items : []
    }
  },
  created(){
    this.fetchData();
  },
  methods : {
    fetchData: function(){
      axios.get("http://localhost:3000/api/user/")
      .then((response)=>{
        this.items = response;
        console.log(response, this.items.data);
      })
      .catch((error)=>{
        console.log('error value is: ', error);
      })
    },
    submitmethod(){
      console.log("sumbitMethod clicked");
    }
  }
}
</script>
