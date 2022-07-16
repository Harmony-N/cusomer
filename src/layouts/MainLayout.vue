<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="no-shadow"  flat>
      <q-toolbar class="toolbar" >
       
       <section style="font-size: 18px; color: #101010; font-weight: 500;line-height: 120%;font-family: 'Gilroy'; font-style: normal;">
          Welcome, Sameze
       </section>
       <section class="api">
        <div>
          <img src="../assets/icon/API.svg" alt="">
        </div>
        <div>
          <img src="../assets/icon/beta.svg" alt="">
        </div>
        <div>
              <q-badge color="white" class="text-black">
              Test Mode <q-toggle class="q-ml-sm"
              v-model="value"
              color="red"
              keep-color
              dense
                      />
              </q-badge>
        </div>
        <div>
          <img src="../assets/icon/bell.svg" alt="">
        </div>
        <div>
          <img src="../assets/icon/person.svg" alt="">
        </div>
        <div>
          <img src="../assets/icon/Polygon_1.svg" alt="">
        </div>
       </section>
       
       
      </q-toolbar>
    </q-header>

    <q-drawer
        show-if-above
        class=" drawer"
      >
        <q-scroll-area class="fit">
          <q-item header class="q-mb-lg q-mr-xl" >
             <q-item-section class="headerO" >
              <div >
                <img src="../assets/icon/Frame_10.svg" alt="">
              </div>
              <div >
              <span style="font-weight: 500; font-size: 14px;font-family: 'Gilroy';color: #222222;">Omni Store</span><br>
              <span style="font-weight: 400; font-size: 10px;font-family: 'Gilroy';color: #666666;">09765WTD098</span>
              </div>
              <div >
                <img src="../assets/icon/Polygon_1.svg" alt="">
              </div>
             </q-item-section>
          </q-item>
          <q-list>
             
            <template v-for="menuItem in menuListItemWithChildren" 
            :key="menuItem.id"
            >
              <q-item  >
              <q-item-section>
              <q-item-label class="menuSection"> {{menuItem.label}} </q-item-label>
               <div>
                <q-item-label v-for="child in menuItem.children" :key="child.index" avatar >
                 
                 <q-item-label class="q-ma-md menusection1" @click="clickMe(child)"> 
                  <q-icon :name="child.icon" class="q-pl-sm"/>
                  {{child.label}}</q-item-label> 
                 </q-item-label>
               </div>  
                </q-item-section>
              </q-item>
              
            </template>
               <q-separator  class="q-mt-xl"/>
               <template v-for="item in subMenu" :key="item.id" >
               <q-item-label class="q-ma-md q-pl-lg menusection1">
                <q-icon :name="item.icon"/>
                {{item.label}}
               </q-item-label>

               </template>
               <q-item-section class="q-ml-lg" >
                <div class="foot1 q-mb-sm q-mt-lg" >
                  Business exposure!
                </div>
                <div class="foot">
                 Get over 500,000 exposure to your 
                business at no cost.
                </div>
                
                
               </q-item-section>

          </q-list>
        </q-scroll-area>
      </q-drawer>


    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'


const menuListItemWithChildren = [
  {
   label:'Onbording',
   children:[{
    label: 'Getting Started',
    icon: 'local_cafe'
   }, {
    label:'Compliance',
    icon: 'gpp_good'
   }]
  },

  {
   label:'Business',
   children:[{
    label: 'Overveiw',
    icon: 'widgets'
   }, {
    label:'Transactions',
    icon: 'payments'
   },{
    label:'Oders',
    icon: 'vignette'
   },{
     label:'Customers',
   icon:'people'
   },{
    label: 'Dispute',
    icon: 'gavel'
   }, {
    label:'Connect',
    icon: 'tap_and_play'
   }]
  },
  
  {
   label:'Seller tools',
   children:[{
    label: 'Payments',
    icon: 'text_snippet'
   }, {
    label:'Analytics',
    icon: 'leaderboard'
   },{
    label: 'Point of Sale(POS)',
    icon:'wysiwyg'
   }, {
    label:'Widget builder',
    icon:'view_sidebar'
   }]
  },  
]

const subMenu=[{
  label: 'Settings',
  icon: 'settings'
},{
  label: 'Audit Log',
  icon:'desktop_windows'
}]


export default defineComponent({
  name: 'MainLayout',

  data(){
    return{
      drawer : ref(false),
      menuListItemWithChildren,
      subMenu,
      value:'false'
    }
  }, methods:{
    clickMe(data){
      console.log('child', data)
    }
  }


})
</script>

<style>
.drawer{
background: #FBFBFB;
width: 265px;
height: 1261px;
}

.foot{
width: 162px;
height: 31px;
font-family: 'Gilroy';
font-style: normal;
font-weight: 400;
font-size: 10px;
line-height: 16px;
color: #222222;
opacity: 0.8;

}

.foot1{
width: 121px;
height: 32px;
font-family: 'Gilroy';
font-style: normal;
font-weight: 600;
font-size: 14px;
line-height: 32px;
color: #1DBC86;
}
.menuSection{
  font-family: 'Gilroy';
font-style: normal;
font-weight: 500;
font-size: 14px;
line-height: 140%;
color: #666666;

}
.menusection1{
  font-family: 'Gilroy';
font-style: normal;
font-weight: 500;
font-size: 14px;
line-height: 140%;
color: #666666;
cursor: pointer;
}

.headerO{
  width: 210px;
  height: 56px;
  display: flex;
  flex-direction: row;
  /* justify-content: space-between; */
  align-items: center;
  padding: 10px;
  gap: 30px;
  background: #FFFFFF;
  border-radius: 4px;
}
.toolbar{
  display: flex;
  flex-direction: row;
  align-content: center;
  justify-content: space-between;
  width: 1175px;
  height: 70px;
  padding: 16px 90px;
  gap: 260px;
  background: #FBFBFB;
}
.api{
  display: flex;
  flex-direction: row;
  align-content: center;
  width: 517px;
  height: 38px;
  padding: 0px;
  gap: 24px;

}

</style>
