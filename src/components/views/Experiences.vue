<template>
  <div>
    <div class="header">
      <img class="header-img" :src="getImageSrc('experiences.png', true)" alt="Experiences Image">
      <h3 class="header-title">{{ headingTitle }}</h3>
      <h4 class="header-subtitle">{{ headingSubtitle }}</h4>
    </div>
    <hr>

    <div class="tabs">
      <div class="tab" :class="{ 'active-tab': activeTab === 'professional' }" @click="setActiveTab('professional')">
        Professional</div>
      <div class="tab" :class="{ 'active-tab': activeTab === 'organizational' }" @click="setActiveTab('organizational')">
        Organizational</div>
    </div>

    <div v-if="activeTab === 'professional'" class="professional">
      <div class="content" v-for="(professional, index) in professionals" :key="index">
        <div class="title-container">
          <div class="title">
            <img class="img" :src="getImageSrc(professional.image)">
            <p class="name">{{ professional.company }}</p>
          </div>
        </div>
        <div class="desc">
          <p class="role">{{ professional.position }} <span class="year">{{ professional.duration }}</span></p>
          <p class="paragraph">{{ professional.description }}</p>
          <ul>
            <li v-for="(responsibility, index) in professional.responsibilities" :key="index">{{ responsibility }}</li>
          </ul>
        </div>
      </div>
    </div>

    <div v-if="activeTab === 'organizational'" class="organizational">
      <div class="content" v-for="(organizational, index) in organizationals" :key="index">
        <div class="title-container">
          <div class="title">
            <img class="img" :src="getImageSrc(organizational.image)">
            <p class="name">{{ organizational.company }}</p>
          </div>
        </div>
        <div class="desc">
          <p class="role">{{ organizational.position }} <span class="year">{{ organizational.duration }}</span></p>
          <p class="paragraph">{{ organizational.description }}</p>
          <ul>
            <li v-for="(responsibility, index) in organizational.responsibilities" :key="index">{{ responsibility }}</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      headingTitle: 'Experiences',
      headingSubtitle: 'My Professional/Organizational Experiences',
      activeTab: 'professional',
      professionals: [
        {
          image: "quantium.png",
          company: "Quantium | Data Science & AI",
          position: "Data Analyst",
          duration: "Dec 2023 - Feb 2024",
          description: "I recently participated in Quantium's Virtual Internship, and it was incredibly useful to understand what it might be like to participate on a data analyst team at Quantium. I worked on a tasks to conduct analyses on a client's transaction dataset and identify customer purchasing behaviours to generate insights and provide commercial recommendations. I used Python and built my Data Visualisation in PowerBI.",
          responsibilities: [
            "Analyzed transaction and customer data to identify trends and inconsistencies.",
            "Developed metrics and examine sales drivers to gain insights into overall sales performance.",
            "Created visualizations and prepare findings to formulate a clear recommendation for the client's strategy.",
            "Defined metrics to select control stores.",
            "Analyzed trial stores against controls.",
            "Used Python for data analysis and visualization and summarize findings and provide recommendations.",
            "Used the Pyramid Principles framework for structuring the report.",
            "Created a report that incorporates data visualizations, key insights, and recommendations."
          ]
        },
        {
          image: "idx.png",
          company: "IDX Partners x Rakamin Academy",
          position: "Data Scientist",
          duration: "Dec 2023",
          description: "I participated in the IDX Partners x Rakamin Academy Virtual Internship as a Data Scientist for one month. During that time, I learned data science methodology and was challenged to master and implement various skills and tools commonly used at IDX Partners, such as Big Data Fundamentals, Statistics & Data Analytics, SQL Querying, R Programming, Python Programming, Machine Learning, and others. As the final task of my internship as a Data Scientist at IDX Partners, I was involved in a project with a lending company. My assignment was to build a model capable of predicting credit risk using a dataset provided by the company, consisting of both accepted and rejected loan data. Additionally, I needed to prepare visual media to present the solution to the client. I ensured that the visual media I created was clear, easily readable, and communicative. The end-to-end solution development was done in python programming language.",
          responsibilities: [
            "Applying data science methodology to analyze transaction and customer data, identifying trends and inconsistencies.",
            "Mastering and implementing various skills and tools, such as Big Data Fundamentals, Statistics & Data Analytics, SQL Querying, R Programming, Python Programming, Machine Learning, and more.",
            "Collaborating with different departments in a lending company project to provide technological solutions.",
            "Building a predictive credit risk model using a dataset containing both accepted and rejected loan data.",
            "Preparing visual media to effectively present the developed solution to the client.",
            "Ensuring clarity, readability, and communicativeness in the visual media created.",
            "Developing the end-to-end solution using my programming language of choice within the Data Science framework/methodology."
          ]
        },
        {
          image: "smrc.png",
          company: "SMRC (Saiful Mujani Research and Consulting)",
          position: "Data Collector",
          duration: "Nov 2023",
          description: "Working as a data collector at SMRC, the national political survey organization, provided me with valuable insights into the field research process. Part of my responsibilities included obtaining the necessary permits from local authorities at various administrative levels, such as subdistrict, urban village, Hamlet, and Neighborhood, to ensure smooth survey operations in designated areas. Additionally, I conducted face-to-face interviews with ten individuals every week to gather their perspectives on their political subjectivity. After collecting this information, I carefully converted it into digital data, ensuring accuracy and ease of analysis. Through this experience, I developed my communication skills while gaining firsthand knowledge of the crucial role data collection plays in informing political research and decision-making processes.",
          responsibilities: []
        }
      ],
      organizationals: [
        {
          image: "himahi.png",
          company: "Himpunan Mahasiswa Hubungan Internasional UPNVJ",
          position: "Youth Development Staff",
          duration: "Jan 2022 - Jan 2023",
          description: "I was part of the Youth Development Department in the Student Association of International Relations at UPNVJ. My role involved helping organize and plan regular tutoring sessions covering academic and non-academic subjects. The goal was to support fellow International Relations students in enhancing their skills and knowledge. Additionally, I contributed to creating a dynamic content plan for social media, highlighting impressive academic projects and creative talents within our faculty.",
          responsibilities: [
            "Assisted in managed and conceived the design of recurring tutoring sessions focusing on both academic topics and non-academic subject, facilitate International Relations students at UPNVJ to develop and improve their knowledge and abilities.",
            "Implemented a dynamic content roadmap on social media, showcasing outstanding academic projects as well as creative talents within the faculty."
          ]
        },
        {
          image: null,
          company: null,
          position: "Youth Development Staff",
          duration: "Jan 2022 - Jan 2023",
          description: "I was part of the Youth Development Department in the Student Association of International Relations at UPNVJ. My role involved helping organize and plan regular tutoring sessions covering academic and non-academic subjects. The goal was to support fellow International Relations students in enhancing their skills and knowledge. Additionally, I contributed to creating a dynamic content plan for social media, highlighting impressive academic projects and creative talents within our faculty.",
          responsibilities: [
            "Assisted in managed and conceived the design of recurring tutoring sessions focusing on both academic topics and non-academic subject, facilitate International Relations students at UPNVJ to develop and improve their knowledge and abilities.",
            "Implemented a dynamic content roadmap on social media, showcasing outstanding academic projects as well as creative talents within the faculty."
          ]
        },
      ],
    };
  },
  methods: {
    setActiveTab(tab) {
      this.activeTab = tab;
    },
    getImageSrc(imageName, isHeaderImage = false) {
      if (!imageName) {
        return null;
      }
      let imagePath;
      try {
        if (isHeaderImage) {
          imagePath = require("@/assets/icons/win95/" + imageName);
        } else {
          imagePath = require("@/assets/images/experiences/professional/" + imageName);
        }
      } catch (error) {
        imagePath = require("@/assets/images/experiences/organizational/" + imageName);
      }
      return imagePath;
    }

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

.header-title {
  text-align: center;
  font-weight: bold;
}

.header-subtitle {
  font-size: 13px;
  color: gray;
  text-align: center;
  padding-top: 10px;
}

/* Tabs */
.tabs {
  display: flex;
  justify-content: center;
  margin-bottom: 10px;
}

.tab {
  cursor: pointer;
  padding: 10px;
  background: rgb(189, 190, 189);
  box-shadow: 1.5px 1.5px black;
  border-top: solid rgb(250, 250, 250) 1.5px;
  border-left: solid rgb(250, 250, 250) 1.5px;
  border-right: solid rgb(90, 90, 90) 1.5px;
  margin-right: 5px;
}

.active-tab {
  background-color: rgb(133, 133, 133);
  color: #fff;
  top: 1px;
}

/* Content */
.title-container {
  display: flex;
  justify-content: center;
}

.title {
  display: inline-block;
  text-align: center;
  /* border: 2px solid white;
  background: rgb(189, 190, 189);
  box-shadow: 1.5px 1.5px black;
  border-top: solid rgb(250, 250, 250) 1.5px;
  border-left: solid rgb(250, 250, 250) 1.5px;
  border-bottom: solid rgb(90, 90, 90) 1.5px;
  border-right: solid rgb(90, 90, 90) 1.5px; */
  padding: 20px;
}

.img {
  width: 130px;
}

.name {
  font-weight: bold;
  text-align: center;
}

.desc {
  padding: 0 30px 0 30px;
  font-size: 15px;
}

.role {
  font-weight: bold;
}

.year {
  float: right;
  font-size: 14px;
  font-weight: normal;
}

.paragraph {
  text-align: justify;
  line-height: 1.3;
}

.desc li {
  list-style: square;
  margin-bottom: 5px;
}

/* Normalize */
h2,
h3,
h4 {
  padding: 0;
  margin: 0;
}

@media screen and (max-width: 1024px) {
  .role {
    display: flex;
    flex-direction: column;
    justify-content: center;
    text-align: center;
    line-height: 1.3;
    padding: 15px 0;
  }

  .name {
    margin-top: 15px;
  }

  .desc {
    padding: 0;
  }

  .desc li {
    display: none;
  }
}
</style>