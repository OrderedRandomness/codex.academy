<template>
  <!-- Navigation -->
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <!-- <div class="container"> -->
    <a href="#" class="navbar-brand" @click.prevent="goHome">
      <img
        class="logo"
        src="img/logo/horizontal_logo.png"
        alt="CodeX Academy Logo"
      />
    </a>
    <button
      class="navbar-toggler navbar-toggler-right"
      type="button"
      @click="toggleMenu"
      data-toggle="collapse"
      data-target="#navbarResponsive"
      aria-controls="navbarResponsive"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon"></span>
    </button>
    <div
      :class="!isOpen ? 'navbar-closed' : ''"
      class="collapse navbar-collapse"
      id="navbarResponsive"
    >
      <ul class="navbar-nav ml-auto">
        <li class="nav-item">
          <a href="#" @click.prevent="goHome" class="nav-link">Home</a>
        </li>
        <li class="nav-item">
          <router-link
            v-if="isInternational"
            to="/programs/international"
            class="nav-link"
            >Monthly Plans</router-link
          >
        </li>
        <li class="nav-item dropdown" v-if="!isInternational">
          <a
            href="#"
            class="nav-link dropdown-toggle"
            id="navbarDropdown"
            role="button"
            data-toggle="dropdown"
            aria-haspopup="true"
            aria-expanded="false"
            >Certifications</a
          >
          <div class="dropdown-menu">
            <div class="nav-item">
              <router-link to="/programs/front-end-developer" class="nav-link"
                >Front-End Developer</router-link
              >
            </div>
            <div class="dropdown-divider"></div>
            <div class="nav-item">
              <router-link to="/programs/full-stack-developer" class="nav-link"
                >Full-Stack Developer</router-link
              >
            </div>
            <div class="dropdown-divider"></div>
            <div class="nav-item">
              <router-link to="/programs/full-stack-engineer" class="nav-link"
                >Full-Stack Engineer</router-link
              >
            </div>
            <div class="dropdown-divider"></div>
            <div class="nav-item">
              <router-link to="/programs" class="nav-link">Compare</router-link>
            </div>
          </div>
        </li>

        <li class="nav-item dropdown" v-if="!isInternational">
          <a
            href="#"
            class="nav-link dropdown-toggle"
            id="navbarDropdown"
            role="button"
            data-toggle="dropdown"
            aria-haspopup="true"
            aria-expanded="false"
            >Financing</a
          >
          <div class="dropdown-menu">
            <div class="nav-item">
              <router-link to="/financial-aid" class="nav-link"
                >Deferred Payment</router-link
              >
            </div>
            <div class="dropdown-divider"></div>
            <div class="nav-item">
              <router-link to="/ISA" class="nav-link"
                >Income Sharing</router-link
              >
            </div>
          </div>
        </li>

        <li class="nav-item dropdown" v-if="isInternational">
          <a
            href="#"
            class="nav-link dropdown-toggle"
            id="navbarDropdown"
            role="button"
            data-toggle="dropdown"
            aria-haspopup="true"
            aria-expanded="false"
            >Financial Aid</a
          >
          <div class="dropdown-menu">
            <div class="nav-item">
              <router-link to="/financing/codex" class="nav-link"
                >Student Loans</router-link
              >
            </div>
          </div>
        </li>

        <!-- <li class="nav-item">
          <router-link to="/financial-aid" class="nav-link">Financial Aid</router-link>
        </li>-->

        <li class="nav-item dropdown">
          <a
            href="#"
            class="nav-link dropdown-toggle"
            id="navbarDropdown"
            role="button"
            data-toggle="dropdown"
            aria-haspopup="true"
            aria-expanded="false"
            >About</a
          >
          <div class="dropdown-menu">
            <div class="nav-item">
              <router-link :to="{ path: '/howitworks' }" class="nav-link"
                >How It Works</router-link
              >
            </div>
            <div class="dropdown-divider"></div>
            <div class="nav-item">
              <router-link
                :to="{ path: '/howitworks', hash: '#curriculum' }"
                class="nav-link"
                >Curriculum</router-link
              >
            </div>
            <div class="dropdown-divider"></div>
            <div class="nav-item">
              <router-link
                :to="{ path: '/howitworks', hash: '#timeline' }"
                class="nav-link"
                >Timeline</router-link
              >
            </div>
            <div class="dropdown-divider"></div>
            <div class="nav-item">
              <router-link
                :to="{ path: '/howitworks', hash: '#tech' }"
                class="nav-link"
                >Technologies</router-link
              >
            </div>
            <div class="dropdown-divider"></div>
            <div class="nav-item">
              <router-link
                :to="{ path: '/howitworks', hash: '#internships' }"
                class="nav-link"
                >Internships</router-link
              >
            </div>
          </div>
        </li>

        <!-- <li class="nav-item">
          <router-link to="/howitworks" class="nav-link"
            >How It Works</router-link
          >
        </li>-->

        <!-- <li class="nav-item dropdown">
          <a
            href="#"
            class="nav-link dropdown-toggle"
            id="navbarDropdown"
            role="button"
            data-toggle="dropdown"
            aria-haspopup="true"
            aria-expanded="false"
            >About</a
          >
          <div class="dropdown-menu">
            <div class="nav-item">
              <router-link to="/faqs" class="nav-link">FAQs</router-link>
            </div>
            <div class="dropdown-divider"></div>
            <div class="nav-item">
              <router-link to="/team" class="nav-link">Our Team</router-link>
            </div>
            <div class="dropdown-divider"></div>
            <div class="nav-item">
              <router-link to="/contact" class="nav-link"
                >Contact Us</router-link
              >
            </div>
          </div>
        </li>-->

        <!-- <li class="nav-item">
          <router-link to="/testimonials" class="nav-link"
            >Testimonials</router-link
          >
        </li>-->
        <!-- <li class="nav-item">
          <router-link class="nav-link" to="/blog">Blog</router-link>
        </li>-->
        <!-- <li class="nav-item">
          <router-link class="nav-link" to="/contact">Contact</router-link>
        </li>-->

        <li class="nav-item">
          <SelectPlanButton
            text="Apply"
            buttonClass="btn btn-primary btn-block nav-link"
          />
        </li>
      </ul>
    </div>
    <!-- </div> -->
  </nav>
</template>

<script>
import separator from "@/components/layout/separator";
import SelectPlanButton from "@/components/SelectPlanButton";
import { mapGetters } from "vuex";

export default {
  name: "NavBar",
  data: () => ({
    isOpen: false,
  }),
  computed: {
    ...mapGetters(["getBootcamp6", "isInternational"]),
  },
  components: { SelectPlanButton, separator },
  methods: {
    toggleMenu() {
      this.isOpen = !this.isOpen;
    },
    goHome() {
      var home = "/";
      if (this.$router.currentRoute.fullPath === home) return;
      this.$router.push(home);
    },
  },
  watch: {
    $route() {
      this.isOpen = false;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/variables";

#nav {
  z-index: 200000;
  padding: 30px;

  a {
    font-weight: bold;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}

.navbar {
  height: 4.5rem;
}
.navbar img.logo {
  height: 3.1rem;
}

.navbar-nav {
  background-color: $lightGray;
}

@media (max-width: 991.98px) {
  .nav-link,
  .dropdown-toggle {
    font-weight: bold !important;
    margin-bottom: 5px !important;
    text-align: center !important;
  }

  .navbar-closed {
    display: none;
  }
}
</style>
