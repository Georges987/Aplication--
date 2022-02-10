<template>
  <div>
    <template>
      <v-row justify="center">
        <v-dialog v-model="dialog" persistent max-width="600px">
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              rounded
              v-bind="attrs"
              v-on="on"
              class="text-capitalize grey--text lighten-4"
              depressed
            >
              <v-icon small left> add </v-icon>
              add
            </v-btn>
          </template>
          <v-card>
            <v-card-title>
              <span class="text-h5">Project New</span>
            </v-card-title>
            <v-card-text>
              <v-container>
                <v-row>
                  <v-col cols="12" sm="6" md="4">
                    <v-text-field
                      hint="Enter the project name please"
                      label="Project title"
                      prepend-icon="folder"
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12">
                    <v-text-field
                      label="Description"
                      type="textarea"
                      hint="Enter the project description please"
                      prepend-icon="edit"
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12">
                    <v-text-field
                      label="Password"
                      type="password"
                      hint="Confirm the project adding with your password"
                      required
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12" sm="6">
                    <v-menu
                      v-model="dateP"
                      :close-on-content-click="false"
                      max-width="290"
                    >
                      <template v-slot:activator="{ on, attrs }">
                        <v-text-field
                          :value="computedDateFormattedDatefns"
                          clearable
                          label="Formatted with datefns"
                          readonly
                          v-bind="attrs"
                          v-on="on"
                          @click:clear="date = null"
                        ></v-text-field>
                      </template>
                      <v-date-picker
                        v-model="date"
                        @change="dateP = false"
                      ></v-date-picker>
                    </v-menu>
                  </v-col>
                </v-row>
              </v-container>
              <small>*indicates required field</small>
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="grey darken-1" text @click="dialog = false"> Cancel </v-btn>
              <v-btn color="grey darken-1" text @click="dialog = false"> Save </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-row>
    </template>
  </div>
</template>
<script>
import moment from "moment";
import { format, parseISO } from "date-fns";
export default {
  data() {
    return {
      date: format(parseISO(new Date().toISOString()), "yyyy-MM-dd"),
      dialog: false,
      dateP: false,
    };
  },
  computed: {
    computedDateFormattedMomentjs() {
      return this.date ? moment(this.date).format("dddd, MMMM Do YYYY") : "";
    },
    computedDateFormattedDatefns() {
      return this.date ? format(parseISO(this.date), "EEEE, MMMM do yyyy") : "";
    },
  },
};
</script>
