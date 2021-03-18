<template>
  <div>
      <b-navbar toggleable="lg" type="dark" variant="info">
        <b-navbar-brand href="#"><img src="https://defaeroreport.com/wp-content/uploads/2019/07/nasa-logo-web-rgb.png" style="max-width: 10rem;" alt=""></b-navbar-brand>
       
        <router-view />
        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
 <div>Coronal Mass Ejection (CME)</div>
        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav class="ml-auto">
            <b-nav-form>
              <b-form-input size="sm" class="mr-sm-2" placeholder="Search"></b-form-input>
              <b-button size="sm" class="my-2 my-sm-0" type="submit" variant="warning " >Search</b-button>
            </b-nav-form>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
    <body background="https://addons.cdn.mozilla.net/user-media/previews/full/215/215878.png?modified=1551714865">
    <hr />
    <div class="container">
      <b-row>
        />

        <h1 style="color:#EA7316"></h1></b-row>
      
        <br /><br />
      
        <b-row cols-lg="5">
            
          <b-card
            v-for="user in userList"
            :key="user.results"
            title=""
            img-src="https://png.pngtree.com/png-vector/20190130/ourlarge/pngtree-astronaut-wearing-a-spacesuit-playing-with-a-model-of-a-spaceship-png-image_587742.jpg"
            img-alt=""
            img-top
            tag="article"
            style="max-width: 20rem;"
            class="mb-2"
            bg-variant="light"
            colspan="12"
            
          >
            ID : {{ user.activityID }}<br /><br />
            {{ user.catalog }}<br /><br />
            Time: {{ user.startTime }}<br /><br />
            {{ user.note }}
            <a :href="user.link"
            
              ><br /><br />
               <hr /><b-button variant="info">ข้อมูลเพิ่มเติม</b-button></a
            >
          </b-card>
          
        </b-row>
     
     </div>
    </body>
     </div>
  
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      userList: null,
    };
  },
  mounted() {
    let url =
      "https://api.nasa.gov/DONKI/CME?startDate=yyyy-MM-dd&endDate=yyyy-MM-dd&api_key=DEMO_KEY";
    axios
      .get(url)
      .then((response) => {
        this.userList = response.data;
      })
      .catch();
    (err) => {
      console.log(err);
    };
  },
};
</script>
<style>



</style>
