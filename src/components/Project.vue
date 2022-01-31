<template>
  <q-card square class="fit q-pa-none q-ma-none shadow-5">
    <q-card-section class="q-pa-none q-ma-none launchit-gradient">
      <div class="row justify-center items-center content-center">
        <div class="col-11">
          <q-btn
            flat
            dense
            no-caps
            :ripple="false"
            class="fit"
            @click="updateProjectsState"
          >
            <div class="text-h6 text-center text-secondary">
              Projects
            </div>
          </q-btn>
        </div>
      </div>
    </q-card-section>
    <q-card-section class="q-pa-none q-ma-none bg-secondary">
      <div class="row justify-center items-center content-center">
        <div class="col-12">
          <q-list
            bordered
            class="fit"
            v-for="(project, idx) in projects"
            :key="idx"
          >
            <q-expansion-item :default-opened="false" group="projects">
              <template v-slot:header>
                <q-item-section avatar>
                  <q-avatar size="xl" v-if="project.logo">
                    <img :src="project.logo">
                  </q-avatar>
                  <q-avatar
                    v-else
                    :class="project.iconBackgroundColor"
                    text-color="white"
                    size="xl"
                    :icon="project.icon"
                  />
                </q-item-section>

                <q-item-section>
                  <q-item-label class="text-h6">{{project.name}}</q-item-label>
                  <q-item-label class="text-h8">{{project.tagline}}</q-item-label>
                </q-item-section>
              </template>

              <q-card square>
                <q-card-section class="q-pa-none">
                  <div class="fit q-px-sm bg-primary text-white text-h6">
                    Description
                  </div>
                  <div class="fit q-px-sm bg-primary text-white text-h8">
                    <p v-html="project.description"/>
                  </div>
                </q-card-section>
                <q-card-section class="q-pa-none">
                  <div class="fit q-px-sm bg-primary text-white text-h6">
                    Languages, Frameworks & APIs
                  </div>
                  <div>
                    <q-chip
                      square
                      v-for="(item, idx) in project.stack"
                      :key="idx"
                      text-color="white"
                      :label="item.label"
                      :color="item.color"
                      :icon="item.icon"
                    />
                  </div>
                </q-card-section>
                <q-card-section class="q-pa-none">
                  <div class="fit q-px-sm bg-primary text-white text-h6">
                    Repo & Demo Links
                  </div>
                </q-card-section>
                <q-card-section class="q-pa-none">
                  <div class="row fit justify-center">
                    <div
                      v-for="(button, idx) in project.buttons"
                      :key="idx"
                      class="column col"
                    >
                      <q-btn
                        no-caps
                        :label="button.label"
                        :icon="button.icon"
                        class="fit"
                        type="a"
                        target="_blank"
                        :href="button.link"
                      />
                    </div>
                  </div>
                </q-card-section>
              </q-card>
            </q-expansion-item>
            <q-separator />
          </q-list>
        </div>
      </div>
    </q-card-section>
  </q-card>
</template>

<script>
export default ({
  name: 'Project',
  data () {
    return {
      projects: [
        {
          name: 'qKard',
          tagline: 'Stand out amongst the crowd!',
          description: 'A web app for users to easily generate Contactless Business Cards.<br>1. Input contact information<br>2. Generate .vcf file<br>3. Host .vcf file<br>4. Generate QR code with embeded link to .vcf file',
          icon: 'qr_code_2',
          iconBackgroundColor: 'bg-orange-7',
          stack: [
            {
              label: 'Vue.js',
              color: 'green',
              icon: 'code'
            },
            {
              label: 'Python',
              color: 'yellow-8',
              icon: 'code'
            },
            {
              label: 'Stripe API',
              color: 'purple-5',
              icon: 'api'
            },
            {
              label: 'Quasar',
              color: 'blue',
              icon: 'view_in_ar'
            },
            {
              label: 'AWS S3',
              color: 'orange-9',
              icon: 'dns'
            },
            {
              label: 'AWS CI/CD',
              color: 'orange-9',
              icon: 'dns'
            },
            {
              label: 'AWS Route 53',
              color: 'orange-9',
              icon: 'dns'
            },
            {
              label: 'AWS API Gateway',
              color: 'orange-9',
              icon: 'api'
            }
          ],
          buttons: [
            {
              label: 'Repo',
              icon: 'ion-logo-github',
              link: 'https://github.com/LaunchIt-Studio/qkard-frontend'
            },
            {
              label: 'Try It!',
              icon: 'language',
              link: 'https://qkard.launchit.studio/#/'
            }
          ],
          state: false
        },
        {
          name: 'Resume',
          tagline: 'Resume/Portfolio Site',
          description: '',
          icon: 'work',
          iconBackgroundColor: 'bg-blue',
          stack: [
            {
              label: 'Vue.js',
              color: 'green',
              icon: 'code'
            },
            {
              label: 'Quasar',
              color: 'blue',
              icon: 'view_in_ar'
            },
            {
              label: 'AWS S3',
              color: 'orange-9',
              icon: 'dns'
            },
            {
              label: 'AWS Code Pipeline',
              color: 'orange-9',
              icon: 'dns'
            },
            {
              label: 'AWS Route 53',
              color: 'orange-9',
              icon: 'dns'
            },
            {
              label: 'AWS CI/CD',
              color: 'orange-9',
              icon: 'dns'
            }
          ],
          buttons: [
            {
              label: 'Repo',
              icon: 'ion-logo-github',
              link: 'https://github.com/flunkout-dvlpr/resume'
            }
          ],
          state: false
        },
        {
          name: 'Barz Bot',
          tagline: 'Turn your favorite lyrics into art!',
          description: '',
          icon: 'queue_music',
          iconBackgroundColor: 'spotify-gradient',
          stack: [
            {
              label: 'Vue.js',
              color: 'green',
              icon: 'code'
            },
            {
              label: 'Quasar',
              color: 'blue',
              icon: 'view_in_ar'
            },
            {
              label: 'Spotify API',
              color: 'green-5',
              icon: 'api'
            },
            {
              label: 'Genius API',
              color: 'black',
              icon: 'api'
            },
            {
              label: 'AWS S3',
              color: 'orange-9',
              icon: 'dns'
            },
            {
              label: 'AWS Code Pipeline',
              color: 'orange-9',
              icon: 'dns'
            },
            {
              label: 'AWS Route 53',
              color: 'orange-9',
              icon: 'dns'
            },
            {
              label: 'AWS CI/CD',
              color: 'orange-9',
              icon: 'dns'
            }
          ],
          buttons: [
            {
              label: 'FE',
              icon: 'ion-logo-github',
              link: 'https://github.com/flunkout-dvlpr/barz-bot-frontend'
            },
            {
              label: 'BE',
              icon: 'ion-logo-github',
              link: 'https://github.com/flunkout-dvlpr/barz-bot-backend'
            },
            {
              label: 'Try It!',
              icon: 'language',
              link: 'https://www.barzbot.app/#/'
            }
          ],
          state: false
        },
        {
          name: 'J.A.R.V.I.S. Alarm',
          tagline: 'Wake up!, Tony Stark style',
          description: '',
          icon: 'alarm',
          iconBackgroundColor: 'jarvis-gradient',
          stack: [
            {
              label: 'Python',
              color: 'yellow-8',
              icon: 'code'
            },
            {
              label: 'Raspberry Pi',
              color: 'red-8',
              icon: 'memory'
            },
            {
              label: 'CRON JOB',
              color: 'grey-8',
              icon: 'update'
            }
          ],
          buttons: [
            {
              label: 'Repo',
              icon: 'ion-logo-github',
              link: 'https://github.com/flunkout-dvlpr/jarvis'
            }
          ],
          state: false
        },
        {
          name: 'Just Wipes Companion App',
          tagline: '',
          description: '',
          icon: 'sanitizer',
          iconBackgroundColor: 'justwipes-gradient',
          stack: [
            {
              label: 'Vue.js',
              color: 'green',
              icon: 'code'
            },
            {
              label: 'Quasar',
              color: 'blue',
              icon: 'view_in_ar'
            },
            {
              label: 'AWS SNS',
              color: 'orange-9',
              icon: 'dns'
            },
            {
              label: 'AWS S3',
              color: 'orange-9',
              icon: 'dns'
            },
            {
              label: 'AWS Code Pipeline',
              color: 'orange-9',
              icon: 'dns'
            },
            {
              label: 'AWS Route 53',
              color: 'orange-9',
              icon: 'dns'
            },
            {
              label: 'AWS CI/CD',
              color: 'orange-9',
              icon: 'dns'
            }
          ],
          buttons: [
            {
              label: 'FE',
              icon: 'ion-logo-github',
              link: 'https://github.com/flunkout-dvlpr/just-wipes-webapp-frontend'
            },
            {
              label: 'BE',
              icon: 'ion-logo-github',
              link: 'https://github.com/flunkout-dvlpr/just-wipes-webapp-backend'
            },
            {
              label: 'Try It!',
              icon: 'language',
              link: 'http://www.justwipes.com.s3-website.us-east-2.amazonaws.com/#/'
            }
          ],
          state: false
        },
        {
          name: 'Bot The Bartender',
          tagline: 'Twitter bot for drink recommendations',
          description: '',
          icon: 'smart_toy',
          iconBackgroundColor: 'bg-orange-9',
          stack: [
            {
              label: 'Python',
              color: 'yellow-8',
              icon: 'code'
            },
            {
              label: 'AWS EB',
              color: 'orange-9',
              icon: 'memory'
            }
          ],
          buttons: [
            {
              label: 'Repo',
              icon: 'ion-logo-github',
              link: 'https://github.com/flunkout-dvlpr/twitter-fix-me-a-drink'
            },
            {
              label: 'Try It!',
              icon: 'language',
              link: 'https://twitter.com/BotTheBartender'
            }
          ],
          state: false
        },
        {
          name: 'Spotify Remote',
          tagline: 'A physical Spotify remote',
          description: '',
          icon: 'settings_remote',
          iconBackgroundColor: 'spotify-gradient',
          stack: [
            {
              label: 'Vue.js',
              color: 'green',
              icon: 'code'
            }
          ],
          buttons: [
            {
              label: 'Repo',
              icon: 'ion-logo-github',
              link: 'https://github.com/flunkout-dvlpr/spotify-remote'
            },
            {
              label: 'Demo',
              icon: 'language',
              link: 'https://www.instagram.com/p/B-qm9KggbFx/?utm_source=ig_web_copy_link'
            }
          ],
          state: false
        }
      ]
    }
  },
  methods: {
    openProject (idx) {
      console.log(idx)
      this.projects.forEach((project, index) => {
        if (idx === index) {
          this.projects[index].state = true
        } else {
          this.projects[index].state = false
        }
      })
    },
    updateProjectsState () {
      const currentState = this.projects[0].state
      this.projects.forEach(project => {
        if (currentState) {
          project.state = false
        } else {
          project.state = true
        }
      })
    }
  }
})
</script>
