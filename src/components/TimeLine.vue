<template lang="pug">
  .container
    h1.title Derek's Story

    p Hi there! My name is Derek and I am a Software Developer!

    p But I wasn't always a software developer. I've done lots of different things.

    p I'm a trekkie and my favourite character is Jean-Luc Picard, but I think "Chief" is cool too.

    #wordtree

    p Working on serveral projects such as:

    b-list-group
      b-list-group-item 
        a(href="http://WhoJimmy.com") WhoJimmy.com
      b-list-group-item
        a(href="https://Mintbean.io") Mintbean.io
      b-list-group-item
        | Flutter based communcation aid app
    
    #timeline.mt-3
</template>
<script src="https://www.gstatic.com/charts/loader.js"></script>
<script>
export default {
  created() {
    setTimeout(() => this.load(), 500);
  },
  methods: {
    load() {
      google.load("visualization", "1.0", {
        packages: ["wordtree", "timeline"]
      });

      // Set a callback to run when the Google Visualization API is loaded.
      google.setOnLoadCallback(this.drawChart);
    },
    drawChart() {
      this.drawWordChart();
      this.drawTimeline();
    },

    drawTimeline() {
      var container = document.getElementById("timeline");
      var chart = new google.visualization.Timeline(container);
      var dataTable = new google.visualization.DataTable();
      dataTable.addColumn({ type: "string", id: "Job" });
      dataTable.addColumn({ type: "string", id: "Company" });
      dataTable.addColumn({ type: "date", id: "Start" });
      dataTable.addColumn({ type: "date", id: "End" });
      dataTable.addRows([
        [
          "High School Student",
          "High School",
          new Date(1999, 1, 1),
          new Date(2004, 1, 1)
        ],
        [
          "Crew Trainer and Kitchen Lead",
          "McDonalds",
          new Date(2002, 1, 1),
          new Date(2004, 1, 1)
        ],
        [
          "Automotive Worker and Inspetor",
          "SKD Automotive",
          new Date(2004, 1, 1),
          new Date(2008, 1, 1)
        ],
        [
          "College Student",
          "Durham College",
          new Date(2008, 1, 1),
          new Date(2011, 1, 1)
        ],
        ["Personal", "Family Care", new Date(2011, 1, 1), new Date(2016, 1, 1)],
        [
          "College Student",
          "Durham College",
          new Date(2016, 1, 1),
          new Date(2018, 1, 1)
        ],
        [
          "Software Developer",
          "Oiika",
          new Date(2017, 1, 1),
          new Date(2019, 1, 1)
        ],
        [
          "Software Developer",
          "E-Data Now!",
          new Date(2018, 1, 1),
          new Date(2019, 1, 1)
        ]
      ]);

      var options = {
        timeline: { showRowLabels: false }
      };

      chart.draw(dataTable, options);
    },
    drawWordChart() {
      // Create the data table.
      var data = google.visualization.arrayToDataTable([
        ["Phrases"],
        ["Derek is a software developer"],
        ["Derek is a business owner"],
        ["Derek is a trekkie"],
        ["Derek likes spicy food"],
        ["Derek likes video games"],
        ["Derek likes the outdoors fishing"],
        ["Derek likes the outdoors hunting"],
        ["Derek likes the outdoors boating"],
        ["Derek likes the outdoors swimming"],
        ["Derek programs in java"],
        ["Derek programs in javascript VueJS"],
        ["Derek programs in javascript NuxtJS"],
        ["Derek programs in javascript ReactJS"],
        ["Derek programs in javascript NodeJS"],
        ["Derek programs in flutter"],
        ["Derek programs in ruby"]
      ]);

      var options = {
        wordtree: {
          format: "implicit",
          word: "Derek"
        }
      };

      var chart = new google.visualization.WordTree(
        document.getElementById("wordtree")
      );
      chart.draw(data, options);
    }
  }
};
</script>