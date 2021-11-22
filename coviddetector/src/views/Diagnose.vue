<template>
   <v-card flat>
    <v-card-text>
      <v-container fluid>
        <v-form action="">
            <v-row>
              <v-col
                v-for="symptom in symptoms"
                :key="symptom"
                cols="12"
                sm="4"
                md="4"
              >
                 <v-checkbox
                  v-model="checks"
                  :label="symptom"
                  color="primary"
                  :value="symptom"
                  hide-details
                ></v-checkbox>
              </v-col>
            </v-row>
            <v-row class="text-center my-4 py-4">
              <v-col>
                <v-btn class="btn btn-primary" @click="submitForm()">
                  <span>Get Results</span>
                </v-btn>
              </v-col>
            </v-row> 
        </v-form>
      </v-container>
    </v-card-text>
    <v-container v-model="submitted">
      <p class="font-weight-bold">
        Diagnostico: {{body}}
      </p>   
    </v-container>
  </v-card>
</template>

<script>
  //import axios from 'axios';
  export default {
    data () {
      return {
        checks: ["placeholder"],
        symptoms: ["Tos","Cefalea","Congestion Nasal","Dificultad Respiratoria",
        "Dolor de garganta","Fiebre","Diarrea","Nauseas","Anosmia Hiposmia","Dolor abdominal",
        "Dolor de articulaciones","Dolor Muscular","Dolor de pecho","Otros sintomas"]   ,
        result: [],
        submitted: false,
        body: [],     
      }
    },
    methods:{
      compareResults(){
        let vm = this;
        vm.body = [];
        vm.symptoms.forEach(function(value){
          if(vm.checks.includes(value)){
            vm.body.push(1);
          }
          else vm.body.push(0);
        });
      },
      submitForm(){
        this.submitted = true;
        this.compareResults(); 
        this.body = {input: this.body};
        /*axios.post('http://localhost:8083/predict-covid',this.body)
        .then((res) =>{
          this.result.push(res);
        })
        .catch((error) => {
          this.result.push(error);
        })
        .finally(() =>{
          this.submitted = true;
        })*/
      }
    }
  }
</script>