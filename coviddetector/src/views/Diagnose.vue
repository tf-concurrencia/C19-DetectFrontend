<template>
   <v-card flat>
    <v-card-text>
      <v-container fluid>
        <v-form action="">
            <v-row>
              <v-col
                cols="12"
                sm="4"
                md="4"
              >
                 <v-checkbox
                  v-model="ex4"
                  label="Tos"
                  color="primary"
                  value="Tos"
                  hide-details
                ></v-checkbox>
              </v-col>
              <v-col
                cols="12"
                sm="4"
                md="4"
              >
                 <v-checkbox
                  v-model="ex4"
                  label="Gripe"
                  color="primary"
                  value="Gripe"
                  hide-details
                ></v-checkbox>
              </v-col>
              <v-col
                cols="12"
                sm="4"
                md="4"
              >
               <v-checkbox
                  v-model="ex4"
                  label="Fiebre"
                  color="primary"
                  value="Fiebre"
                  hide-details
                ></v-checkbox>
              </v-col>
            </v-row>
            <v-row class="mt-12">
              <v-col
                cols="12"
                sm="4"
                md="4"
              >
                <v-checkbox
                  v-model="ex4"
                  label="Dolor de Pecho"
                  color="primary"
                  value="Dolor-Pecho"
                  hide-details
                ></v-checkbox>
              </v-col>
              <v-col
                cols="12"
                sm="4"
                md="4"
              >
                <v-checkbox
                  v-model="ex4"
                  label="XXXX"
                  color="primary"
                  value="XXXX"
                  hide-details
                ></v-checkbox>
              </v-col>
              <v-col
                cols="12"
                sm="4"
                md="4"
              >
                 <v-checkbox
                  v-model="ex4"
                  label="YYYY"
                  color="primary"
                  value="YYYY"
                  hide-details
                ></v-checkbox>
              </v-col>
            </v-row>
        </v-form>
      </v-container>
    </v-card-text>
    <v-container>
        {{ex4}}
    </v-container>
  </v-card>
</template>

<script>
  export default {
    data () {
      return {
        ex4: ["ZZZZ"],
      }
    },
  }
</script>