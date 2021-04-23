<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar class="q-ma-xs row justify-center">
        <div class="col-12 justify-center">
            <div class="row justify-center">
              <q-btn
                round
                no-ripple
                @click="switchImage = !switchImage"
              >
                <q-img
                  transition="flip-left"
                  :src="switchImage ? profileImages[0] : profileImages[1]"
                  style="width: 125px; height: 125px; border-radius: 50%; border: 5px solid #a1a1a1;"
                />
              </q-btn>
            </div>
            <div class="row justify-center text-h6">Julio C. Gonzalez</div>
            <div class="row justify-center text-subtiitle1">Full Stack Software Developer</div>
            <div class="row justify-center text-caption">Houston, TX</div>
        </div>
      </q-toolbar>

      <q-tabs
        dense
        class="bg-secondary text-black"
        v-model="section"
        @input="scrollToSection"
      >
        <q-tab no-caps name="about-me" label="About Me" />
        <q-tab no-caps name="experience" label="Experience" />
        <q-tab no-caps name="projects" label="Projects" />
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
            href="https://github.com/flunkout-dvlpr"
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
            href="https://www.linkedin.com/in/julio-gonzalez-4b2904b0"
          />
        </div>
        <div class="col-xs-3 col-sm-3 col-md-1 col-lg-1 col-xl-1">
          <q-btn
            flat
            class="fit"
            type="a"
            icon="phone"
            size="md"
            href="tel:832-589-5877"
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
            href="mailto:info@juliogonzalez.space"
          />
        </div>
      </q-toolbar>
    </q-footer>

    <q-page-container>
      <router-view />
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
      profileImages: [
        'https://media-exp1.licdn.com/dms/image/C4E03AQH06TWHQ2tZ_w/profile-displayphoto-shrink_400_400/0/1565450126632?e=1624492800&v=beta&t=M2kv1H-Qewc0ZOzBPBHdewWQPxVf8E9PFNBxQc6IoHQ',
        'https://avatars.githubusercontent.com/u/22562966?v=4'
      ]
    }
  },
  methods: {
    scrollToSection (section) {
      console.log(section)
      const element = document.getElementById(section)
      const y = element.getBoundingClientRect().top + window.pageYOffset - 250
      window.scrollTo({ top: y, behavior: 'smooth' })
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
