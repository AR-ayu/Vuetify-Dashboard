<template>
  <div class="dashboard">
    <h1 class="subheading grey--text">Dashboard</h1>

    <v-container class="my-5">

      <v-layout row justify-start class="mb-3">
        <v-btn small flat color="grey" @click="sortBy('title')">
          <v-icon small left>folder</v-icon>
          <span class="caption text-lowercase">By Poetry</span>
        </v-btn>
        <v-btn small flat color="grey" @click="sortBy('person')">
          <v-icon small left>person</v-icon>
          <span class="caption text-lowercase">By Author</span>
        </v-btn>
      </v-layout>
      
      <v-card flat v-for="project in projects" :key="project.title">
        <v-layout row wrap :class="`pa-3 project ${project.status}`">
          <v-flex xs12 md6>
            <div class="caption grey--text">Poetry Name</div>
            <div>{{ project.title }}</div>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <div class="caption grey--text">Author</div>
            <div>{{ project.person }}</div>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <div class="caption grey--text">Due by</div>
            <div>{{ project.due }}</div>
          </v-flex>
          <v-flex xs2 sm4 md2>
            <div class="right">
              <v-chip small :class="`${project.status} white--text my-2 caption`">{{ project.status }}</v-chip>
            </div>
          </v-flex>
        </v-layout>
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
        { title: 'HONEY AND SUGAR', person: 'Rupi Kaur', due: '1st Jan 2019', status: 'ongoing', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'LEAVES OF GRASS', person: 'Walt Whitman', due: '10th Jan 1855', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'AND STILL I RISE', person: 'Maya Angelou', due: '20th Dec 1978', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'THE ESSENTIAL', person: 'Rumi', due: '20th Oct 2004', status: 'overdue', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'A WILDFLOWER WAS BORN', person: 'William Blake', due: '13th Feb 1997', status: 'ongoing', content: 'As I wanderd the forest.The green leaves among.I heard a wild flower.Singing a song.'},
      ]
    }
  },
  methods: {
    sortBy(prop) {
      this.projects.sort((a,b) => a[prop] < b[prop] ? -1 : 1)
    }
  }
}
</script>

<style>

.project.complete{
  border-left: 4px solid #52cbfc;
}
.project.ongoing{
  border-left: 4px solid #fab854;
}
.project.overdue{
  border-left: 4px solid #bb0133;
}
.v-chip.complete{
  background: #52cbfc;
}
.v-chip.ongoing{
  background: #ffaa2c;
}
.v-chip.overdue{
  background: #bb0133;
}

</style>
