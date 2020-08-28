<template>
  <v-dialog max-width="600px" v-model="dialog">
    <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="red lighten-2"
          dark
          v-bind="attrs"
          v-on="on"
        >
          Add New Project
        </v-btn>
      </template>
    <v-card>
      <v-card-title>
        <h2>Add a New Project</h2>
      </v-card-title>
      <v-card-text>
          <v-form class="px-3" ref="form">
              <v-text-field label="Title" v-model="title" prepend-icon="folder" :rules="inputRules"></v-text-field>
              <v-textarea label="information" v-model="content" prepend-icon="edit" :rules="inputRules"></v-textarea>
              
            <v-menu
                v-model="menu1"
                :close-on-content-click="false"
                transition="scale-transition"
                offset-y
                max-width="290px"
                min-width="290px"
                >
                <template v-slot:activator="{ on, attrs }">
                    <v-text-field
                    v-model="dateFormatted"
                    label="Due Date"
                    hint="MM/DD/YYYY format"
                    persistent-hint
                    prepend-icon="event"
                    v-bind="attrs"
                    @blur="date = parseDate(dateFormatted)"
                    v-on="on"
                    :value="due"
                    :rules="inputRules"
                    ></v-text-field>
                </template>
                <v-date-picker v-model="due" no-title @input="menu1 = false"></v-date-picker>
            </v-menu>
              
              
              
              <v-btn flat class="white--text mx-0 mt-3" color="#3CD1C2" @click="submit" loading="loading">Add project</v-btn>
          </v-form>
      </v-card-text>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
name: 'Popup',

  data: () => ({
   title: '',
   content: '',
   due: null,
   inputRules: [
       v => v.length >= 3 || 'Minimum length is 3 characters'
   ],
   loading: false,
   dialog: false,
  }),

  methods: {
    submit() {
        if(this.$refs.form.validate()) {
            // this.loading = true;
            console.log(this.title, this.content)
        }
    },

  }
}
</script>

<style>

</style>