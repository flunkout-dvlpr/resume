<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar class="launchit-gradient q-pa-none q-ma-none">
        <div class="q-py-sm fit row justify-center items-center content-center">
          <div class="q-pb-xs col-12 column justify-center items-center content-center">
            <q-btn
              round
              no-ripple
              @click="switchImage = !switchImage"
            >
              <q-img
                transition="flip-left"
                :src="switchImage ? images.profile : images.avatar"
                :style="`width: 125px; height: 125px; border-radius: 50%; border: 5px solid ${switchImage ? '#303030' : '#ebebeb'}`"
              >
              </q-img>
            </q-btn>
          </div>
          <div class="q-pb-xs col-12 column justify-center items-center content-center">
            <div class="text-center text-h6">{{profile.fullName}}</div>
          </div>
        <div class="q-pb-xs col-12 column justify-center items-center content-center">
          <div class="text-center text-subtiitle1">{{profile.position}}</div>
        </div>
        <div class="q-pb-none col-12 column justify-center items-center content-center">
          <div class="text-center text-caption">{{profile.caption}}</div>
        </div>
        <div class="q-pb-xs col-12 column justify-center items-center content-center">
          <div class="text-center text-caption">{{profile.location}}</div>
        </div>
        </div>
      </q-toolbar>
      <q-tabs
        dense
        v-model="section"
        indicator-color="accent"
        active-color="secondary"
        @input="scrollToSection"
      >
        <q-tab class="col-2" no-caps name="about-me" label="About Me" />
        <q-tab class="col-2" no-caps name="experience" label="Experience" />
        <q-tab class="col-2" no-caps name="projects" label="Projects" />
      </q-tabs>
    </q-header>

    <q-footer elevated>
      <q-toolbar class="q-mx-xs row justify-center">
        <div class="col-xs-3 col-sm-3 col-md-1 col-lg-1 col-xl-1">
          <q-btn
            flat
            class="fit"
            type="a"
            target="_blank"
            icon="ion-logo-github"
            size="md"
            :href="links.github"
          />
        </div>
        <div class="col-xs-3 col-sm-3 col-md-1 col-lg-1 col-xl-1">
          <q-btn
            flat
            class="fit"
            type="a"
            target="_blank"
            icon="ion-logo-linkedin"
            size="md"
            :href="links.linkedin"
          />
        </div>
        <div class="col-xs-3 col-sm-3 col-md-1 col-lg-1 col-xl-1">
          <q-btn
            flat
            class="fit"
            type="a"
            icon="phone"
            size="md"
            :href="`tel:${links.phone}`"
          />
        </div>
        <div class="col-xs-3 col-sm-3 col-md-1 col-lg-1 col-xl-1">
          <q-btn
            flat
            class="fit"
            type="a"
            target="_blank"
            icon="mail"
            size="md"
            :href="`mailto:${links.email}`"
          />
        </div>
      </q-toolbar>
    </q-footer>

    <q-page-container>
      <router-view/>
    </q-page-container>

  </q-layout>
</template>

<script>
export default {
  name: 'MainLayout',
  data () {
    return {
      section: 'about-me',
      switchImage: false,
      profile: {
        fullName: 'Julio C. Gonzalez',
        position: 'Full Stack Dev | Solutions Architect',
        caption: 'Hablo Español!',
        location: 'Houston, TX | Miami, FL'

      },
      links: {
        github: 'https://github.com/flunkout-dvlpr',
        linkedin: 'https://www.linkedin.com/in/julio-gonzalez-4b2904b0',
        phone: '832-589-5877',
        email: 'info@juliogonzalez.space'
      },
      images: {
        profile: 'profile.jpeg',
        avatar: 'avatar.png'
      }
    }
  },
  methods: {
    scrollToSection (section) {
      const element = document.getElementById(section)
      element.scrollIntoView({ behavior: 'smooth', block: 'start' })
      // const scrollWindow = document.getElementById('scroll-section')
      // const y = element.getBoundingClientRect().top
      // scrollWindow.scrollTo({ top: y, behavior: 'smooth' })
      this.$router.push({ path: `/${section}` })
      if (section === 'projects') {
        this.switchImage = false
      } else {
        this.switchImage = true
      }
    }
  },
  mounted () {
    setTimeout(() => { this.switchImage = true }, 800)
  }
}
</script>
