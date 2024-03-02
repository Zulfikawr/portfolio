<template>
    <div class="menu" style="z-index: 1000000">
      <div class="socials">


        <a @click="openWindow('biographyWindow')">
          <div class="bar">
            <img class="social-image" src="@/assets/icons/win95/bio.png" />
            <u>B</u>iography
          </div>
        </a>

        <a @click="openWindow('projectsWindow')">
          <div class="bar">
            <img class="social-image" src="@/assets/icons/win95/projects.png" />
            <u>P</u>rojects
          </div>
        </a>

        <a @click="openWindow('skillsWindow')">
          <div class="bar">
            <img class="social-image" src="@/assets/icons/win95/skills.png" />
            <u>S</u>kills
          </div>
        </a>

        <a @click="openWindow('experiencesWindow')">
          <div class="bar">
            <img class="social-image" src="@/assets/icons/win95/experiences.png" />
            <u>E</u>xperiences
          </div>
        </a>

        <a @click="openWindow('educationsWindow')">
          <div class="bar">
            <img class="social-image" src="@/assets/icons/win95/educations.png" />
            <u>E</u>ducations
          </div>
        </a>

        <a @click="openWindow('certificationsWindow')">
          <div class="bar">
            <img class="social-image" src="@/assets/icons/win95/certifications.png" />
            <u>C</u>ertifications
          </div>
        </a>

        <a @click="openWindow('publicationsWindow')">
          <div class="bar">
            <img class="social-image" src="@/assets/icons/win95/resume.png" />
            <u>P</u>ublications
          </div>
        </a>
      
        <div class="divider"></div>

        <a @click="!showFolderMenu">
        <div v-if="!showFolderMenu" class="back">
          <u>B</u>ack
        </div>
      </a>
  
      </div>
    </div>
  </template>
  <style scoped>
  .menu {
    width: 200px;
    height: 300px;
    background: black;
    background: rgb(195, 195, 195);
    overflow: hidden;
    border-top: solid rgb(250, 250, 250) 2px;
    border-left: solid rgb(250, 250, 250) 2px;
    border-right: solid rgb(90, 90, 90) 1.5px;
    border-bottom: solid rgb(90, 90, 90) 1.5px;
    box-shadow: 1.5px 1.5px black;
    max-height: 100%;
    max-width: 100%;
    align-items: flex-end;
    outline: rgb(222, 222, 222) 1px solid;
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    font-size: 12px;
  }
  
  a {
    color: black;
    text-decoration: none;
  }
  
  .divider {
    width: 100%;
    height: 1px;
    background: rgb(123, 125, 123);
    border-bottom: white solid 1px;
  }
  
  .socials {
    flex-grow: 1;
    cursor: pointer;
  }
  
  .social-image {
    width: 30px;
    height: 30px;
    margin-right: 10px;
    border-radius: 6px;
  }
  
  .bar {
    display: flex;
    flex-direction: row;
    padding: 5px 10px 5px 10px;
    align-items: center;
  }
  
  .bar:hover {
    background: rgb(0, 0, 118);
    color: white;
  }

  .back {
    text-align: left;
    padding-top: 12px;
    padding-left: 12px;
  }
  </style>

<script>
export default {
  methods: {
    openWindow(windowId) {
      const payload = {
        windowState: "open",
        windowID: windowId,
      };
      this.$store.commit("setWindowState", payload);
    },
  },
};
</script>

  