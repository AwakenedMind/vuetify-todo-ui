<template>
  <div class="dashboard">
    <v-container class="my-5">
      <v-layout row class="mb-3">
        <v-row align="center" justify="start">
          <span class="body-2 grey--text mr-4">Filter by</span>
          <v-btn
            small
            color="black mr-2"
            class="white--text grey darken-3"
            @click="sortBy('title')"
          >
            <v-icon left small>mdi-folder</v-icon>
            <span class="caption text-lowercase">Project Name</span>
          </v-btn>
          <v-btn
            small
            color="black mr-2"
            class="white--text grey darken-3"
            @click="sortBy('person')"
          >
            <v-icon left small>mdi-account</v-icon>
            <span class="caption text-lowercase">person</span>
          </v-btn>
        </v-row>
      </v-layout>

      <v-card flat class="px-3" v-for="project in projects" :key="project.title">
        <v-row row wrap :class="`pa-3 project ${project.status}`">
          <v-col cols="12" md="6">
            <div class="caption grey--text">Project title</div>

            <div>{{project.title}}</div>
          </v-col>

          <v-col xs="2">
            <div class="caption grey--text">Person</div>

            <div>{{project.person}}</div>
          </v-col>

          <v-col xs="2">
            <div class="caption grey--text">Due Date</div>

            <div>{{project.due}}</div>
          </v-col>

          <v-col xs="2">
            <div class="caption grey--text">Status</div>
            <div class="right">
              <v-chip
                small
                color="project.status"
                :class="`${project.status} white--text caption my-2`"
              >{{project.status}}</v-chip>
            </div>
          </v-col>
        </v-row>
        <v-divider></v-divider>
      </v-card>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      projects: [
        {
          title: "Design a new website",
          person: "Rob",
          due: "1st Jan 2019",
          status: "ongoing",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!"
        },

        {
          title: "Code up the homepage",
          person: "Chun Li",
          due: "10th Jan 2019",
          status: "complete",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!"
        },

        {
          title: "Design video thumbnails",
          person: "Ryu",
          due: "20th Dec 2018",
          status: "complete",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!"
        },

        {
          title: "Get a job",
          person: "Aatrox",
          due: "20th Oct 2018",
          status: "overdue",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!"
        }
      ]
    };
  },
  methods: {
    sortBy(prop) {
      this.projects.sort((a, b) => (a[prop] < b[prop] ? -1 : 1));
    }
  }
};
</script>

<style>
.project.complete {
  border-left: 4px solid #26de81;
}
.project.ongoing {
  border-left: 4px solid orange;
}
.project.overdue {
  border-left: 4px solid tomato;
}

.v-chip.ongoing {
  background: orange !important;
}

.v-chip.complete {
  background: #26de81 !important;
}

.v-chip.overdue {
  background: #fc5c65 !important;
}
</style>