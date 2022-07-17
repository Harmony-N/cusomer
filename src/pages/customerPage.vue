<template>
  <q-page class="flex">
    <section class="mainSection">
    <section class="mainBody">
      <div class="row firstE">
      <div class="col-2 customer">
        Customer: 0
      </div>
      <div class="col-5 secondE">
       <q-input
       borderless
       no-outline
       dense
       filled
       bg-color="white"
        placeholder="Search using name or transaction ID"
       
      >
        <template v-slot:prepend>
          <q-icon name="search" />
        </template>
      </q-input>
      </div>
      <div class="col q-ml-xl">
        <img src="../assets/icon/Frame_7.svg" alt="">
        <img src="../assets/icon/Frame.svg" alt="" class="q-ml-md">
      </div>
    </div>

    <div class="thirdE">
      <q-tabs
          v-model="tab"
          dense
          no-caps
          class="text-black"
          active-color="green"
          indicator-color="green"
          align="justify-left"
          narrow-indicator
        >
          <q-tab name="all" label="All" />
          <q-tab name="blacklisted" label="Blacklisted" />
          
        </q-tabs>
        <q-separator />
        <q-tab-panels v-model="tab" animated>
          <q-tab-panel name="mails">
          </q-tab-panel>
        </q-tab-panels>
    </div>

   
    <div >
      <q-table
      flat
      table-class="firthE q-ml-xm"
      :rows="rows"
      :columns="columns"
      :pagination="initialPagination"
      rows-per-page-options="0"
      table-header-class='headerClass'
      card-container-class="containerClass"
      row-key="customer"
      >
      <template v-slot:body="props">
       <q-tr :props="props">
       <q-td key="customer" :props="props">
       {{props.row.customer}}
       </q-td>
       <q-td key="email" :props="props">
    {{props.row.email}}
       </q-td>
       <q-td key="phone" :props="props"> 
     {{props.row.phone}}
       </q-td>
       <q-td key="date" :props="props"> 
     {{props.row.date}}
       </q-td>
       <q-td key="menu" :props="props"> 
       <q-btn flat label="...">
        <q-menu
          transition-show="scale"
          transition-hide="scale"
        >
          <q-list style="max-width: 113px">
            <q-item clickable @click="onItemClick">
              <q-item-section>View</q-item-section>
            </q-item>
            <q-item clickable @click="onItemClick">
              <q-item-section>Blacklist</q-item-section>
            </q-item>
          </q-list>
        </q-menu>
      </q-btn>
       </q-td>
       
       </q-tr>
       </template>

     </q-table>
    

    </div>
    <div class="sixE"> 
    <q-pagination
      
      outline
      color="rgba(0, 0, 0, 0.85)"
      active-color="green"
      v-model="current  "
      :max="5"
      direction-links
    />

    </div>
      

    </section>
    </section>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
import axios from 'axios'



export default defineComponent({
  name: 'IndexPage',
  data (){
    return{
        tab: 'all',
        current: (1),
        users: [],
        columns:[
           {name:'customer', label:'Customer', field:'customer',align :'left', style:'width: 245px;color: #101010;height:72px;font-family:Gilroy;font-size: 14px; background-color:#FFFFFF;'},
           {name:'email', label:'Email Address', field:'email',align :'left',style:'width: 245px;color: #101010;height:72px;font-family:Gilroy;font-size: 14px;background-color:#FFFFFF;'},
           {name:'phone', label:'Phone Number', field:'phone',align :'left',style:'width: 245px;color: #101010;height:72px;font-family:Gilroy;font-size: 14px;background-color:#FFFFFF;'},
           {name:'date', label:'Date', field:'date',align :'left',style:'width: 214px;color: #101010;height:72px;font-family:Gilroy;font-size: 14px;background-color:#FFFFFF;'},
            {name:'menu', label:'', field:'menu',align :'left',style:'width: 68px;color: #101010;height:72px;font-family:Gilroy;font-size: 14px;background-color:#FFFFFF;cursor:pointer'}
        ], 
        rows:[],
        initialPagination: {
        rowsPerPage: 6
        
      }
    }
  }, mounted(){
    axios.get('https://dummyjson.com/users')
    .then((resp) =>{
        this.users=resp.data.users
        console.log(resp.data.users)

        const users= resp.data.users

        users.forEach(user => {
           
          const {firstName,email,phone,birthDate} = user
      this.rows.push(
         {
        customer:firstName,
        email,
        phone,
        date:birthDate,
        menu: '...'
      } 
      )  
        });
    }).catch((e)=>{
        console.log(`Display error: ${e}`)
    })
  }, methods:{
    onItemClick(){
        console.log('This item was clicked')
    }
  }
  

})
</script>

<style>
.mainSection{
  width: 1095px;
  height: 869px;
  padding: 36px 16px 24px 24px;
  background: #FBFBFB;
}
.mainBody{
  width: 1045px;
  height: 729px;
  background: #FFFFFF;
  padding: 8px;

}
.firstE{
  width: 1029px;
  height: 58px;
  background: #FFFFFF;
  padding: 8px 12px;
 
}
.secondE{
  width: 480px;
  height: 42px;
 
  background: #FBFBFB;
}
.customer{
  width: 137px;
height: 24px;
font-family: 'Gilroy';
font-style: normal;
font-weight: 600;
font-size: 15px;
line-height: 24px;
color: #222222;
}
.thirdE{
  width: 1005px;
  height: 46px;
}
.fourthE{
  width: 1017px;
 height: 44px;
 font-family: 'Gilroy';
font-style: normal;
font-weight: 400;
font-size: 14px;
color: #666666;
line-height: 140%;


}
.firthE{
  display: flex;
flex-direction: column;
align-items: flex-start;
padding: 0px;
/* gap: 12px; */
width: 1017px;
height: 555px;

  
}

.sixE{
  width: 1055px;
  height: 44px;
  background: #FFFFFF;
  padding: 10px;
  display: flex;
  justify-content: end;
 
}
.headerClass{
font-family: 'Gilroy';
font-style: normal;
font-weight: 400;
font-size: 14px;
color: #666666;
background-color:#FBFBFB;
height: 44px;
line-height: 140%;
}

</style>
