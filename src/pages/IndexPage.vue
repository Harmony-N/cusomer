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

    <div class="fourthE">
      <div class="row q-ml-md q-mt-md">
      <div class="col">Customer Name</div>
      <div class="col">Email Address</div>
      <div class="col">Phone Number</div>
      <div class="col">Date</div>
    </div>

    </div>

    <div class="firthE">
      <div class="firthEE">
        <div>
          <img src="../assets/icon/Group.svg" alt=""/>
        </div>
        <div style="font-size: 18px;font-weight: 400;font-family: 'Gilroy';line-height: 120%;color: #101010;">
          You have no customers yet
        </div>
        <div style="font-size: 14px;font-weight: 400;font-family: 'Gilroy';line-height: 120%;color: #666666;">
          Your customer list will appear here
        </div>
      </div>

    </div>
    <div class="sixE"> 
    <q-pagination
      outline
      color="rgba(0, 0, 0, 0.85)"
      active-color="green"
      v-model="current"
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

export default defineComponent({
  name: 'IndexPage',
  data (){
    return{
        tab: 'all',
        current: (1)
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
  width: 1029px;
  height: 505px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.firthEE{
  width: 225px;
  height: 506px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.sixE{
  width: 1055px;
  height: 44px;
  background: #FFFFFF;
  padding: 10px;
  display: flex;
  justify-content: end;
}
</style>
