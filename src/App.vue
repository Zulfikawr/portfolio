<template>
  <div id="app">

    <!-- Booting -->
    <!-- <Boot v-if="isLoading" />
    <div v-else> -->

      <!-- Top Navbar -->
      <top-navbar id="top-navbar"></top-navbar>

      <!-- Windows -->
      <div class="screen" id="screen" @click="deinitWindows">
        <div
          v-for="window in windows"
          :key="window.key"
          :aria-label="window.displayName"
        >
          <component
            :is="window.windowComponent"
            :nameOfWindow="window.windowId"
            :content_padding_bottom="isMobile ? window.windowContentPadding.mobile?.bottom ?? window.windowContentPadding.bottom : window.windowContentPadding.bottom"
            :content_padding_left="isMobile ? window.windowContentPadding.mobile?.left ?? window.windowContentPadding.left : window.windowContentPadding.left"
            :content_padding_right="isMobile ? window.windowContentPadding.mobile?.right ?? window.windowContentPadding.right : window.windowContentPadding.right"
            :content_padding_top="isMobile ? window.windowContentPadding.mobile?.top ?? window.windowContentPadding.top : window.windowContentPadding.top"
            :id="window.windowId"
            :style="{
              position: window.position,
              left: isMobile ? window.positionXMobile : window.positionX,
              top: isMobile ? window.positionYMobile : window.positionY,
            }"
            :folderContent="window.folderContent"
            :folderSize="window.folderSize"
            v-if="windowCheck(window.windowId)"
          >
            <component :is="window.windowContent" slot="content"> </component>
          </component>
        </div>
        <app-grid></app-grid>
      </div>

      <!-- Start menu & Navbar -->
      <StartMenu
        v-if="$store.getters.getActiveWindow == 'Menu'"
        style="position: absolute; z-index: 9999; left: 0; bottom: 30px">
      </StartMenu>
      <navbar style="position: absolute; bottom: 0; z-index: 9999" id="navbar" />

      <!-- Popup message -->
      <Popup v-if="showDefaultPopup" :message="defaultPopupMessage" />
      <Popup v-if="isMobile && showMobilePopup" :message="mobilePopupMessage" />
      <Popup v-if="mailSent && showMailSentPopup" :message="mailSentPopupMessage" />
    <!-- </div> -->
  </div>
</template>


<script>
// Import Components //

// Template //
import Boot from "./components/template/Boot";
import Navbar from "./components/windows/Navbar";
import AppGrid from "./components/windows/AppGrid";
import Window from "./components/template/Window";
import Mail from "./components/template/Mail";
import StartMenu from "./components/windows/StartMenu";
import Popup from "./components/template/Popup";

// Windows //
import Bio from "./components/views/Bio";
import Resume from "./components/views/Resume";
import Projects from "./components/views/Projects";
import Publications from "./components/views/Publications";
import Certifications from "./components/views/Certifications";
import Educations from "./components/views/Educations";
import Experiences from "./components/views/Experiences";
import Skills from "./components/views/Skills";

// Projects //
import IDX from "./components/windows/projects/data_analysis/idx";
import Quantium from "./components/windows/projects/data_analysis/quantium";
import Win95Portfolio from "./components/windows/projects/webdev/win95portfolio";
import VSCodePortfolio from "./components/windows/projects/webdev/vscodeportfolio";
import LandingPage from "./components/windows/projects/webdev/landingpage";

export default {
  name: "App",
  data: function () {
    return {
      isLoading: true,
      windows: this.$store.getters.getWindows,
      windowComponents: {},
      defaultPopupMessage: 'Click and drag windows to interact',
      mobilePopupMessage: 'Access the site from a desktop for the best experience',
      mailSentPopupMessage: 'Mail has been sent!',
    };
  },
  components: {
    Boot,
    Navbar,
    AppGrid,
    Window,
    StartMenu,
    Popup,
    Bio,
    Resume,
    Projects,
    Publications,
    Certifications,
    IDX,
    Quantium,
    Mail,
    Educations,
    Experiences,
    Skills,
    Win95Portfolio,
    VSCodePortfolio,
    LandingPage,

    // TopNavbar,
  },
  computed: {
    style() {
      return {
        "--fullscreen": this.$store.getters.getFullscreenWindowHeight,
      };
    },
    isMobile() {
      return window.innerWidth <= 768;
    },
    isDesktop() {
      return window.innerWidth >= 768;
    },
    showDefaultPopup() {
      return this.isDesktop;
    },
    showMobilePopup() {
      return this.isMobile;
    },
    mailSent() {
      return this.$store.state.mailSent;
    },
    showMailSentPopup() {
      return this.mailSent;
    }
  },
  mounted() {
    if (this.isMobile) {
      this.isLoading = false;
    } else
    setTimeout(() => {
      this.isLoading = false;
    }, 5000);

    /*-------------------------------------------------*\
        This fixes height problems for mobile devices 

        Code is detecting height of navbar and setting
        respective heights of screen
    \*-------------------------------------------------*/

    let navbar = document.getElementById("navbar");
    let topnavbar = document.getElementById("top-navbar");
    let topNavbarHeight = topnavbar.clientHeight;
    let navbarHeight = navbar.clientHeight;

    document.getElementById("screen").style.height =
      window.innerHeight - navbarHeight - topNavbarHeight + "px";

    window.addEventListener("resize", () => {
      let vh = window.innerHeight * 0.01;
      document.documentElement.style.setProperty("--vh", `${vh}px`);
    });

    function resetHeight() {
      document.body.style.height = window.innerHeight + "px";
      document.documentElement.style.height = window.innerHeight + "px";
    }

    window.addEventListener("resize", resetHeight);
    this.$store.commit(
      "setFullscreenWindowHeight",
      window.innerHeight - navbarHeight - topNavbarHeight + "px"
    );

    // Open biographyWindow only if not in mobile mode
    if (!this.isMobile) {
      this.openWindow("biographyWindow");
    }

    if (this.isMobile) {
      this.$store.dispatch("setAllWindowsFullscreen", true);
    }

  },
  methods: {
    openWindow(windowId) {
      const payload = {
        windowState: "open",
        windowID: windowId,
      };
      this.$store.commit("setWindowState", payload);
    },

    windowCheck(windowId) {
      if (this.$store.getters.getWindowById(windowId).windowState == "open") {
        return true;
      }
    },

    deinitWindows() {
      if (this.$store.getters.getActiveWindow == "Menu") {
        console.log("deinitWindows");
        this.$store.commit("setActiveWindow", "");
        setTimeout(() => {
          this.$store.commit("zIndexIncrement", "");
        }, 0);
      }
    },
  },
};
</script>

<style>
/*----------------*\
    CSS Imports
\*----------------*/
@import "./assets/css/utils/normalize.css";
@import "./assets/css/windows/app.css";
@import "./assets/css/windows/window.css";
@import "./assets/css/windows/appgrid.css";

@font-face {
  font-family: "MS Sans Serif";
  src: url("~@/assets/fonts/MS-Sans-Serif.ttf");
}

/*---------------*\
     Utilities
\*---------------*/

html {
  overflow: hidden;
}

#app {
  font-family: "MS Sans Serif";
  font-weight: 400;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  width: 100%;
  height: calc(var(--vh, 1vh) * 100);
  flex-direction: column;
}

.screen {
  width: 100%;
  position: relative;
  z-index: 999;
}

::-webkit-scrollbar {
  width: 15px;
  background: repeating-conic-gradient(
      rgb(189, 190, 189) 0% 25%,
      rgb(255, 255, 255) 0% 50%
    )
    50% / 2px 2px;
}
::-webkit-scrollbar-thumb {
  background: rgb(189, 190, 189);
  border-top: solid rgb(250, 250, 250) 1.5px;
  border-left: solid rgb(250, 250, 250) 1.5px;
  border-bottom: solid rgb(90, 90, 90) 1.5px;
  border-right: solid rgb(90, 90, 90) 1.5px;
  outline: rgb(219, 219, 219);
}

@media only screen and (max-width: 600px) {
  ::-webkit-scrollbar {
  width: 10px;
  background: repeating-conic-gradient(
      rgb(189, 190, 189) 0% 25%,
      rgb(255, 255, 255) 0% 50%
    )
    50% / 2px 2px;
}
}

/*-------------------------------------------*\
    Fullscreen
\*-------------------------------------------*/

.fullscreen {
  left: 0 !important;
  position: relative;
  display: block;
  top: 0 !important;
  right: 0 !important;
}

.fullscreen iframe {
  height: 500px;
}

@media only screen and (max-width: 600px) {
  .fullscreen iframe {
    height: 200px;
  }
}
</style>