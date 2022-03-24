
<template>
    <form action="" class="container_1">
      <div id="Error_cont" v-if="errorz.length" style="background:#FF3256;" >
            -Password Does not contain required characters
            <li v-for="error in errorz" style="list-style:none" >
                - {{error}}
            </li>
        </div>
      <h3 align="center" >Set new Password</h3>
      <label>Email</label><br>
      <input type="email" placeholder="email@gmail.com"><br>
      <label>New Password</label><br>        
      <input :type="type" name="" id="" v-model="password" placeholder="password" ><br>
      <input type="checkbox" @click="type_changer" name="" id="show" v-model="text_type"><label for="show">Show Password</label><br>
      <input type="button" name="" id="" value="Change Password" style="background-color:#93E6BA;margin-left: 220px;">
    </form>
</template>

<script >
// var errors=[];
 export default {
  data() {
    return {
      password: "",
      errorz:[],
      text_type:false,
      type:"password"
    }
  },
  watch: {
    // whenever question changes, this function will run
    password(str, c2) {
      this.errorz=[];
      let err=false;
      const rgx1=/([A-Z])/;
      const rgx2=/([a-z])/;
      const rgx3=/([0-9])/;
      const rgx4=/(\W)/;
      if(!str.match(rgx1)){
        this.errorz.push("Your Password must contain atleast 1 upperase letter")
      }
      if(!str.match(rgx2)){
        this.errorz.push("Your Password must contain atleast 1 small letter")
      }
      if(!str.match(rgx3)){
        this.errorz.push("Your Password must contain atleast 1 Number")
      }
      if(!str.match(rgx4)){
        this.errorz.push("Your Password must contain atleast 1 special character (&^@$@) letter ")
      }
      if (str.length<=8 || str.length>=50) {
        this.errorz.push("Your Password must contain min 8 and 50 characters")
      }
    }
  },
  methods:{
    type_changer(){
      let now=this.text_type
      console.log(now)
        if (now==true) {
          this.type="password"
        }else{
          this.type="text";
        }
    }
  }
}
</script>
<style>
.container_1{
  font-size: 14px;
  margin-top: 50px;
  margin-left: auto;
  margin-right: auto;
  width: 350px;
  height: auto;
  outline: dashed 1px black;
}

</style>
