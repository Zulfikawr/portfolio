<template>
  <div>
    <div class="header">
      <img class="header-img" :src="getImageSrc('projects.png', true)" alt="Projects Image">
      <h3 class="header-title">{{ headerTitle }}</h3>
      <h4 class="header-subtitle" v-html="headerSubtitle"></h4>
    </div>
    <hr>

    <div class="content" v-for="(project, index) in projects" :key="index">
      <a class="title" @click="openWindow(project.windowId)">
        {{ project.title }}
      </a>
      <iframe :src="project.iframeSrc" type="application/pdf"></iframe>
      <div class="tags">
        <button v-for="(tags, tagIndex) in project.tags" :key="tagIndex">
          <label>{{ tags }}</label>
        </button>
      </div>
      <p class="desc">{{ project.desc }}</p>
      <div class="link">
        <button @click="openWindow(project.windowId)">
          <img src='@/assets/icons/win95/directory.png'>
          <label>Documentation</label>
        </button>
        <button @click="redirectToGitHub(project.githubLink)">
          <img src='@/assets/icons/social/github.png'>
          <label>GitHub</label>
        </button>
      </div>
      <hr>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      headerTitle: 'Projects',
      headerSubtitle: 'A complete lists of my projects. You can also see it in <a href="https://github.com/muhammad-zulfikar">GitHub</a>',
      projects: [
        {
          title: "Retail Analytics - Data Analysis at Quantium",
          windowId: "quantiumWindow",
          iframeSrc:
            "https://drive.google.com/file/d/1JaaSKAHkucj1SOx4q9HzT562fE0sHLJv/preview",
          tags: [
            "Data Analysis",
            "Python",
            "Power BI",
            "PowerPoint",
          ],
          desc:
            "I recently participated in Quantium's virtual internship. I worked on a project to conduct analyses on a client's transaction dataset and identify customer purchasing behaviours to generate insights and provide commercial recommendations. I used Python and built my Data Visualisation in PowerBI.",
          githubLink: "https://github.com/muhammad-zulfikar/quantium",
        },
        {
          title: "Credit Risk Predictive Model - Data Scientist at ID/X Partners",
          windowId: "idxWindow",
          iframeSrc: "https://zulfikawr.github.io/idx_choropleth/",
          tags: ["Data Analysis", "Python", "Data Visualization"],
          desc:
            "During my internship at ID/X Partners, I had the chance to work on an exciting final project. I was given datasets of approved and rejected loan applications. My goal was to create a model that could predict if a loan application would be approved or rejected. I used my skills in Python programming to build this predictive model.",
          githubLink:
            "https://github.com/muhammad-zulfikar/idxpartners_finalproject",
        },
        // Add more projects here
      ],
    };
  },
  methods: {
    getImageSrc(imageName, isHeaderImage = false) {
      let imagePath;
      if (isHeaderImage) {
        imagePath = require("@/assets/icons/win95/" + imageName);
      } else {
        imagePath = require("@/assets/images/projects/" + imageName);
      }
      return imagePath;
    },
    openWindow(windowId) {
      const payload = {
        windowState: "open",
        windowID: windowId,
      };
      this.$store.commit("setWindowState", payload);
    },
    redirectToGitHub(githubLink) {
      window.open(githubLink, "_blank"); 
    },
  }
};
</script>

<style scoped>

/* Global */
.header,
.content {
  padding: 20px 0;
}

/* Header */
.header {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.header-img {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 60px;
  padding-bottom: 20px;
}

.header-title{
  text-align: center;
  font-weight: bold;
}

.header-subtitle {
  font-size: 13px;
  color: gray;
  text-align: center;
  padding-top: 10px;
}

/* Content */
.title {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  text-decoration: none;
  color: inherit;
  font-weight: bold;
  font-size: 16px;
  cursor: pointer;
}

iframe {
  width: 100%;
  height: 300px;
  margin-top: 20px;
}

.tags {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  text-align: center;
}

.tags button {
  display: flex;
  align-items: center;
  padding: 5px;
  padding-bottom: 2.5px;
  height: 25px;
  margin: 10px 5px 2px 5px;
  width: auto;
  border: 2px solid white;
  background: rgb(189, 190, 189);
  box-shadow: 1.5px 1.5px black;
  border-top: solid rgb(250, 250, 250) 1.5px;
  border-left: solid rgb(250, 250, 250) 1.5px;
  border-bottom: solid rgb(90, 90, 90) 1.5px;
  border-right: solid rgb(90, 90, 90) 1.5px;
}

.tags label {
  padding-top: 2px;
  font-size: 12px;
  padding-left: 3px;
}

.desc {
  font-size: 15px;
  line-height: 1.3;
  text-align: justify;
}

.link {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  text-align: center;
}

.link button {
  display: flex;
  align-items: center;
  padding: 5px;
  padding-bottom: 2.5px;
  height: 30px;
  margin: 10px 5px 30px 5px;
  width: auto;
  border: 2px solid white;
  background: rgb(189, 190, 189);
  box-shadow: 1.5px 1.5px black;
  border-top: solid rgb(250, 250, 250) 1.5px;
  border-left: solid rgb(250, 250, 250) 1.5px;
  border-bottom: solid rgb(90, 90, 90) 1.5px;
  border-right: solid rgb(90, 90, 90) 1.5px;
  cursor: pointer;
}

.link img {
  height: 22px;
  padding-bottom: 2px;
  cursor: pointer;
}

.link label {
  padding-top: 2px;
  padding-left: 5px;
  font-size: 13px;
  cursor: pointer;
}

.link button:hover {
  background-color: darkgray;
}

/* Normalize */
h2,
h3,
h4 {
  padding: 0;
  margin: 0;
}

/* Media query */
@media screen and (max-width: 1024px) {
  .tags button {
    margin-bottom: 20px;
  }
  iframe {
  height: 200px;
}
}

</style>