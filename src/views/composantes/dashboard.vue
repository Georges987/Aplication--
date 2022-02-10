<template>
  <div class>
    <v-parallax src="/vbanner.jpg" class="text-center font-italic"> <span class="display-3 font-weight-bold">Welcome <span class="red--text">user</span></span> </v-parallax>
    <v-row class="pa-5">
      <v-col cols="12" sm="8" md="8" lg="8">
        <v-card dark class="pa-5">
          <v-card-title> Your progress this week </v-card-title>
          <v-sheet
            class="v-sheet--offset mx-auto pa-5"
            elevation="5"
            max-width="calc(100% - 32px)"
          >
            <v-sparkline
              :labels="labels"
              auto-draw-duration="3000"
              :value="value"
              color="red"
              :gradient="['#EC8B9C', '#FF660088', '#221FEA']"
              line-width="1"
              smooth="2"
              auto-draw
              padding="16"
            ></v-sparkline>
          </v-sheet>
        </v-card>
      </v-col>
      <v-col class="ml-15" cols="12" sm="4" md="3" lg="3">
        <v-date-picker
          dark
          v-model="picker"
          year-icon="mdi-calendar-blank"
          prev-icon="mdi-skip-previous"
          next-icon="mdi-skip-next"
        ></v-date-picker>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" sm="8" md="8" lg="8">
        <v-expansion-panels dark class="ml-5">
            <v-expansion-panel class="bor" v-for="project in projects" :key="project.title" :class="` project ${project.status} `">
              <v-expansion-panel-header>
                <v-card dark flat>
                  <v-card-title class="grey--text text-capitalize"> {{ project.title }} </v-card-title>
                  <v-card-content class="grey--text text-capitalize ml-4">
                    {{ project.dueDate }}
                  </v-card-content>
                  <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-chip id="chips" :class="` ${project.status} caption`"> {{ project.status }} </v-chip>
                  </v-card-actions>
                </v-card>
              </v-expansion-panel-header>
              <v-expansion-panel-content> {{ project.content }} </v-expansion-panel-content>
            </v-expansion-panel>
            <v-divider></v-divider>
        </v-expansion-panels>
      </v-col>
      <v-col cols="12" sm="3" md="3" lg="3" class="ml-15">
        <v-card dark class="pa-5">
          <v-card-title class="grey--text draken-4"> Add project </v-card-title>
          <v-card-content>
            Add new project for this week. Try to finish it before due date. Good luck
          </v-card-content>
          <v-card-actions class="pa-7">
            <v-spacer></v-spacer>
            <addPRO />
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
    <v-card dark> </v-card>
  </div>
</template>
<script>
import addPRO from "@/components/addPRO";
export default {
  components: { addPRO },
  data: () => ({
    picker: new Date(Date.now() - new Date().getTimezoneOffset() * 60000)
      .toISOString()
      .substr(0, 10),
    labels: [
      "Monday",
      "Tuesday",
      "Wednesday",
      "Thursday",
      "Friday",
      "Saturday",
      "Sunday",
    ],
    value: [10, 850, 90, 100, 150, 500, 0],
    projects: [
      {
        title: "Realize an description",
        dueDate: "Wednesday, December 11th 2022",
        status: "complete",
        content:
          "lorem ipsumj ljelbg negl ekngken nkengk ngknk l n nn nke ngklnkengmnùeznk ngmqib brgrbgbrmobg ioqbiogbodbqr iùbioqbreb erig ùrig ùpgrg0",
      },
      {
        title: "Create a website",
        dueDate: "Thursday, April 2nd 2022",
        status: "overdue",
        content:
          "lorem ipsumj ljelbg negl ekngken nkengk ngknk l n nn nke ngklnkengmnùeznk ngmqib brgrbgbrmobg ioqbiogbodbqr iùbioqbreb erig ùrig ùpgrg0",
      },
      {
        title: "Doing the thing",
        dueDate: "Monday, June 1st 2022",
        status: "complete",
        content:
          "lorem ipsumj ljelbg negl ekngken nkengk ngknk l n nn nke ngklnkengmnùeznk ngmqib brgrbgbrmobg ioqbiogbodbqr iùbioqbreb erig ùrig ùpgrg0",
      },
      {
        title: "Kill somebody",
        dueDate: "Sunday, March 7th 2022",
        status: "complete",
        content:
          "lorem ipsumj ljelbg negl ekngken nkengk ngknk l n nn nke ngklnkengmnùeznk ngmqib brgrbgbrmobg ioqbiogbodbqr iùbioqbreb erig ùrig ùpgrg0",
      },
      {
        title: "Design my car",
        dueDate: "Friday, January 18th 2021",
        status: "overdue",
        content:
          "lorem ipsumj ljelbg negl ekngken nkengk ngknk l n nn nke ngklnkengmnùeznk ngmqib brgrbgbrmobg ioqbiogbodbqr iùbioqbreb erig ùrig ùpgrg0",
      },
      {
        title: "Solve this course",
        dueDate: "Thursday, September 10th 2022",
        status: "ongoing",
        content:
          "lorem ipsumj ljelbg negl ekngken nkengk ngknk l n nn nke ngklnkengmnùeznk ngmqib brgrbgbrmobg ioqbiogbodbqr iùbioqbreb erig ùrig ùpgrg0",
      },
    ],
  }),
};
</script>
<style>

  .project.complete{
    border-left: 4px solid green;
  }

  .project.ongoing{
    border-left: 4px solid orange;
  }

  .project.overdue{
    border-left: 4px solid red;
  }

  #chips.v-chip.complete{
    background: rgb(95, 241, 95);
  }

  #chips.v-chip.ongoing{
    background: rgb(211, 160, 65);
  }

  #chips.v-chip.overdue{
    background: rgb(224, 67, 67);
  }

</style>