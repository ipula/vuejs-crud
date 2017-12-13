<template>
   <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <section class="card">
        <div class="row pull-right">
            <!-- <div class="row">
                <li v-for="testData in testDatas">{{testData.first_name}}</li></br>
            </div> -->
            <div class="form-group row">
               <div class="col-md-12">
                  <label for="l30">Name</label>
                  <input type="text" class="form-control" placeholder="Name" id="l1" v-model="message.text1" name="vehicle_cust_name">
                </div>
            </div>
            </br>
            <div class="form-group row">
               <label for="l30">Job</label>
                    <div class="col-md-12">
                        <input v-model="message.text2" class="form-control" placeholder="Job">
                    </div>
            </div>
        
            <div class="form-group row">
              <div class="col-sm-6">
                    <button v-on:click="say(message)">Say what</button>
              </div>
            </div>
        </div>
          </section>
  </div>
  
</template>
<script>
export default {
  name: "Module1",
  data() {
    return {
      testDatas: [],
      message: {},
      msg: "Welcome to Your test rout"
    };
  },
  created: function() {
    this.apiData();
  },
  methods: {
    apiData: function() {
      this.$http
        .get("https://reqres.in/api/users?page=2")
        .then(response => response.json())
        .then(data => {
          this.testDatas = data.data;
        });
    },
    say: function(message) {
      this.$http
        .post("https://reqres.in/api/users", {
          name: message.text1,
          job: message.text1
        })
        .then(response => response.json())
        .then(data => {
          console.log(data);
        });
    }
  }
};
</script>

<style>

</style>


