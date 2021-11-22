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
              <v-col v-if="!submitted">
                <v-btn class="btn btn-primary" @click="submitForm()">
                  <span>Diagnosticar</span>
                </v-btn>
              </v-col>
              <v-col v-else>
                <v-progress-circular 
                indeterminate
                :size="50"
                color="purple">
                </v-progress-circular>
              </v-col>
            </v-row> 
        </v-form>
      </v-container>
    </v-card-text>
    <v-container class="text-center">
      <h4>Resultado</h4>
      <v-card 
      class="my-4"
      :color="result===''? 'white' : (result===0? 'green':'warning')">
        <v-card-text class="font-weight-bold">
         {{body}} => {{result}}
        </v-card-text>  
      </v-card>
       
    </v-container>
  </v-card>
</template>

<script>
  import axios from 'axios';
  export default {
    data () {
      return {
        checks: ["placeholder"],
        symptoms: ["Tos","Cefalea","Congestion Nasal","Dificultad Respiratoria",
        "Dolor de garganta","Fiebre","Diarrea","Nauseas","Anosmia Hiposmia","Dolor abdominal",
        "Dolor de articulaciones","Dolor Muscular","Dolor de pecho","Otros sintomas"]   ,
        result: "",
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
        axios.post('http://localhost:8084/predict',this.body)
        .then((res) =>{
          this.result = res.rpta;
        })
        .catch((error) => {
          this.result = error;
        })
        .finally(() =>{
          this.submitted = false;
        })
      }
    }
  }
</script>