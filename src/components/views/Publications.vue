<template>
  <div>
    <div class="header">
      <img class="header-img" :src="getImageSrc('resume.png', true)" alt="Publications Image">
      <h3 class="header-title">{{ headerTitle }}</h3>
      <h4 class="header-subtitle">{{ headerSubtitle }}</h4>
    </div>
    <hr>

    <div class="tabs">
      <div class="tab" :class="{ 'active-tab': activeTab === '2023' }" @click="setActiveTab('2023')">
        2023
      </div>
      <div class="tab" :class="{ 'active-tab': activeTab === '2022' }" @click="setActiveTab('2022')">
        2022
      </div>
      <div class="tab" :class="{ 'active-tab': activeTab === '2021' }" @click="setActiveTab('2021')">
        2021
      </div>
    </div>

    <div class="content">
        <div v-for="(publication, index) in filteredPublications" :key="index">
          <a class="title" :href="publication.link" target="_blank">
            {{ publication.title }}
          </a>
          <div class="tags">
            <button v-for="(tags, tagIndex) in publication.tags" :key="tagIndex">
              <label>{{ tags }}</label>
            </button>
          </div>
          <p class="abstract">{{ publication.abstract }}<a :href="publication.link"> Read more</a></p>
          <hr>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      headerTitle: 'Publications',
      headerSubtitle: 'A complete collection of my academic works, including papers, articles, journals, and publications. Mostly IR-related stuff',
      activeTab: '2023',
      publications: [
        {
          title: "Revolution in Military Affairs: Kebangkitan dan Revolusi China dalam Militer dan Ekonomi yang mengancam Amerika Serikat",
          link: "https://medium.com/@2110412039/revolution-in-military-affairs-kebangkitan-dan-revolusi-china-dalam-militer-dan-ekonomi-yang-9d3122af8dcf",
          tags: ["RMA", "International Relations", "Realism"],
          year: '2022',
          abstract:
            "China menerapkan strategi Revolusi Militer asimetris dengan fokus pada peperangan informasi dan anti-access/area denial (A2/AD) untuk mengatasi keunggulan teknologi AS. Kemajuan militer China, meskipun terhambat oleh korupsi dan ketergantungan impor teknologi, telah meningkatkan kepercayaan diri negara tersebut dalam melindungi kepentingan nasionalnya.",
        },
        {
          title: "Invasi Rusia ke Ukraina pada 2022 dalam Perspektif Hukum Internasional",
          link: "https://drive.google.com/file/d/1k-Y_BqvNn-sTYNF7rcMiwQnMgQ4jGN_f/view?usp=drive_link",
          tags: ["International Law", "Invasion", "Conflict", "Realism"],
          year: '2023',
          abstract:
            "Invasi Rusia ke Ukraina pada tahun 2022 merupakan pelanggaran serius terhadap hukum internasional. Tindakan ini tidak memiliki pembenaran dan merupakan penggunaan kekuatan dan kekerasan yang ilegal, serta merupakan aksi agresi. Alasan Rusia untuk melakukan invasi, seperti menjaga keamanan negara dan penduduknya dari ancaman NATO, tidak dapat diterima berdasarkan hukum internasional.",
        },
        {
          title: "Peran ASEAN dalam Mengatasi Masalah Human Security Terorisme: Studi Kasus Bom Bali",
          link: "https://drive.google.com/file/d/13oXXtt4-9XPtHcYH87QQoznuzg0WNu1K/view?usp=drive_link",
          tags: ["ASEAN", "Human Security", "Institutionalism"],
          year: '2021',
          abstract:
            "Terorisme merupakan ancaman serius bagi keamanan manusia di Asia Tenggara. ASEAN telah menunjukkan komitmennya dalam memerangi terorisme dengan membentuk berbagai kelompok kerja dan regulasi, seperti ASEAN Ministerial Meeting on Transnational Crime (AMMTC), ASEAN Political-Security Community (APSC), Asean Convention on Counter Terrorism (ACCT), dan ASEAN Regional Forum (ARF).",
        },
        {
          title: "Konflik Panjang Palestina-Israel dan Restrukturisasi DK PBB",
          link: "https://medium.com/@2110412039/konflik-panjang-palestina-israel-dan-restrukturisasi-dk-pbb-35fc1a14a18b",
          tags: ["Humanitarian Law", "Conflict", "UNSC", "Global Security", "Realism"],
          year: '2023',
          abstract:
            "Konflik Palestina-Israel, bermula dari peristiwa tahun 1948, telah berkembang menjadi krisis multiaspek yang ditandai oleh pengusiran massal, tantangan kemanusiaan, dan kejahatan perang yang dilakukan oleh Israel, khususnya di Gaza.",
        },
        {
          title: "Digitalisasi sebagai Pendorong Utama Soft Power Negara di Era Globalisasi",
          link: "https://drive.google.com/file/d/1vphxSb5wJ7yY1IjrX6VjxDsutwlqgD8P/view?usp=drive_link",
          tags: ["Digitalization", "Digital Diplomacy", "Soft Power", "Foreign Policy"],
          year: '2023',
          abstract:
            "Di era globalisasi, digitalisasi menjadi pendorong utama soft power negara. Media sosial dan platform digital memperluas jangkauan pengaruh budaya, nilai-nilai, dan kebijakan luar negeri suatu negara.",
        },
        {
          title: "Upaya Indonesia dalam Meningkatkan Strategi Keamanan Siber melalui Kerjasama Indonesia-Inggris",
          link: "https://drive.google.com/file/d/1iDUcs9hzYC9-ryzEiiW8VY1QD9b7dw8G/view?usp=drive_link",
          tags: ["Diplomacy", "Cyber Security", "Bilateral"],
          year: '2022',
          abstract:
            "Penyalahgunaan internet oleh oknum-oknum tertentu telah menyebabkan berbagai kejahatan siber atau yang sering disebut sebagai perang siber. Menyadari ancaman yang bersifat internasional tersebut, Indonesia terlibat dalam kerjasama bilateral dengan Inggris, untuk mengatasi dan memerangi ancaman siber yang semakin meningkat.",
        },
        {
          title: "Diplomasi Lingkungan Indonesia di Era Kepemimpinan Susilo Bambang Yudhoyono: Studi Kasus Kabut Asap Lintas Batas di Asia Tenggara",
          link: "https://drive.google.com/file/d/1qu0XSJXj-5yI75potqLYjSWDLSHXNHf9/view?usp=drive_link",
          tags: ["Diplomacy", "Climate", "Foreign Policy", "SBY"],
          year: '2022',
          abstract:
            "Diplomasi lingkungan Indonesia di era SBY mengalami dinamika dalam menangani kabut asap lintas batas. Kebakaran hutan dan lahan di Indonesia menyebabkan kabut asap yang berdampak pada negara tetangga, memicu ketegangan diplomatik.",
        },
        {
          title: "The Importance of Cyber Security Awareness: COVID-19 Case Study Analysis",
          link: "https://medium.com/@2110412039/the-importance-of-security-training-for-employees-a-case-study-analysis-of-security-incidents-adf70a4b5d27",
          tags: ["Cybersecurity", "Cyberattacks", "COVID 19"],
          year: '2023',
          abstract:
            "Information security stands as a critical pillar for business continuity in today's digital landscape, yet individuals, often the weakest link, remain susceptible to cyberattacks. This article explores the imperative of safety training for employees by examining cases of safety accidents resulting from a lack of knowledge.",
        },
        {
          title: "Sistem Nilai Tukar Mengambang: Studi Kasus Krisis Finansial Asia 1998",
          link: "https://drive.google.com/file/d/16ic9qSz55Qz7_jeiE3mjnO-BNpMYI6-U/view?usp=drive_link",
          tags: ["Financial Crisis", "IMF"],
          year: '2022',
          abstract:
            "Sistem finansial dianut berdasarkan berbagai aspek dan faktor yang berbeda di setiap negara, sehingga setiap negara memiliki sebuah kebijakannya masing-masing dalam menentukan sistem finansial apa yang terbaik untuk negaranya. Fenomena krisis finansial Asia 1997-1998 terjadi berawal dari Thailand yang terjadi penurunan nilai tukar Baht dan membuat berbagai permasalahan yang dirasakan dampaknya oleh negara-negara lain.",
        },
        {
          title: "Komunikasi Kepemimpinan",
          link: "https://drive.google.com/file/d/1F5zvugipA9rnrxNyh0FkXUJ7b79KZMoX/view?usp=drive_link",
          tags: ["Leadership", "Communication"],
          year: '2022',
          abstract:
            "Komunikasi menjadi aspek dasar dalam organisasi sekaligus hal yang esensial dan sangat penting untuk dipelajari oleh pemimpin karena komunikasi berperan signifikan bagi organisasi dan tidak dapat dipisahkan dari seluruh kegiatan di dalamnya. Fungsi komunikasi yang mewadahi proses interaksi timbal balik bagi sebuah organisasi, ditentukan atau dipengaruhi oleh bagaimana gaya komunikasi kepemimpinan yang diterapkan.",
        },
        {
          title: "Pengaruh Penggunaan Sosial Media Instagram terhadap Perilaku Remaja",
          link: "https://drive.google.com/file/d/1s6PZjkJTucWH2U_jUDufdXsSOgTygfE2/view?usp=drive_link",
          tags: ["Social Media", "Behaviour"],
          year: '2021',
          abstract:
            "Penggunaan Instagram bukan hanya berdampak positif namun juga menimbulkan dampak negatif pada remaja, terutama pada kondisi perilakunya. Instagram dapat memengaruhi perilaku remaja karena konten-konten yang ada di Instagram baik positif maupun negatif tersebar tanpa ada yang mengontrolnya.",
        },
      ],
    };
  },
  computed: {
      filteredPublications() {
        return this.publications.filter(pub => pub.year === this.activeTab);
      },
  },
  methods: {
    setActiveTab(tab) {
      this.activeTab = tab;
    },
    getImageSrc(imageName, isHeaderImage = false) {
      let imagePath;
      if (isHeaderImage) {
        imagePath = require("@/assets/icons/win95/" + imageName);
      } else {
        imagePath = require("@/assets/images/publications/" + imageName);
      }
      return imagePath;
    }
  }
}
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
  font-size: 13px;
  justify-content: left;
  padding-top: 20px;
}

.tab {
  cursor: pointer;
  padding: 7px 5px 5px 5px;
  border-top: solid rgb(250, 250, 250) 2px;
  border-left: solid rgba(250, 250, 250) 2px;
  border-right: solid rgb(90, 90, 90) 2px;
  border-bottom: solid rgb(250, 250, 250) 1px;
  /* border-top-right-radius: 3px;
  border-top-left-radius: 3px; */
}

.active-tab {
  font-weight: bold;
  border-bottom: 2px solid rgb(195, 195, 195);
  position: relative;
  z-index: 9999;
}

/* Content */
.content {
  border-top: solid rgb(250, 250, 250) 2px;
  border-left: solid rgb(250, 250, 250) 2px;
  border-bottom: solid rgb(90, 90, 90) 2px;
  border-right: solid rgb(90, 90, 90) 2px;
  padding: 10px;
  margin-top: -2px;
  position: relative;
  z-index: 1;
}

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
  margin: 20px 0;
}


.tags {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  text-align: center;
  margin-bottom: 30px;
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

.abstract {
  font-size: 14px;
  text-align: justify;
  margin-bottom: 30px;
  padding: 20px;
}

.abstract a {
  color: inherit;
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
  .abstract {
    margin-top: 20px;
    padding: 5px;
  }
}

</style>