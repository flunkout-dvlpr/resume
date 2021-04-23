<template>
  <q-page>
    <div class="row justify-center items-center content-center">
      <q-card square id="about-me" class="q-ma-md col-md-6 col-xs-11 shadow-5">
        <q-card-section class="q-pa-xs q-ma-none bg-primary text-white">
          <div class="row justify-around">
            <div class="col-12 text-h6 text-center">
              About Me
            </div>
          </div>
        </q-card-section>
        <q-card-section class="q-pa-xs q-ma-xs">
          <div class="row justify-around">
            <div class="col-8">
              {{textPlaceHolder}}
            </div>
          </div>
        </q-card-section>
      </q-card>

      <q-card square id="experience" class="q-ma-md col-md-6 col-xs-11 shadow-5">
        <q-card-section class="q-pa-xs q-ma-none bg-primary text-white">
          <div class="row justify-around">
<!--             <div class="col-12 text-h6 text-center">
              Experience
            </div> -->
            <div class="col-12">
              <q-btn
                flat
                dense
                no-caps
                :ripple="false"
                class="text-h6 text-center fit"
                label="Experience"
                @click="updateExperiencesState"
              />
            </div>
          </div>
        </q-card-section>
        <q-list
          bordered
          class="fit"
          v-for="(experience, idx) in experiences"
          :key="idx"
        >
          <q-expansion-item :value="experience.state">
            <template v-slot:header>
              <q-item-section avatar>
                <q-avatar size="xl" v-if="experience.logo">
                  <img :src="experience.logo">
                </q-avatar>
                <q-avatar
                  v-else
                  :class="experience.iconBackgroundColor"
                  text-color="white"
                  size="xl"
                  :icon="experience.icon"
                />
              </q-item-section>

              <q-item-section>
                <q-item-label class="text-h6">{{experience.companyName}}</q-item-label>
                <q-item-label class="text-h8">{{experience.period}}</q-item-label>
              </q-item-section>

            </template>

            <q-card>
              <q-card-section class="q-pa-sm">
                <div class="fit q-px-md bg-primary rounded-borders text-white text-h6">About The Employer</div>
                <div class="q-px-lg q-py-sm bg-accent rounded-borders">{{experience.description}}</div>
              </q-card-section>
              <q-card-section class="q-pa-sm">
                <div class="fit q-px-md bg-primary rounded-borders text-white text-h6">Role & Responsibilities</div>
                <div class="q-px-lg q-py-sm bg-accent rounded-borders">{{experience.role}}</div>
              </q-card-section>

              <q-card-actions>
                <div class="fit q-px-md bg-primary rounded-borders text-white text-h6">References</div>
                <q-list
                  bordered
                  class="fit"
                  v-for="(reference, idx) in experience.references"
                  :key="idx"
                >
                  <q-item
                    class="rounded-borders"
                    dense
                  >
                    <q-item-section avatar>
                      <q-avatar size="50px">
                        <img :src="reference.profileImage">
                      </q-avatar>
                    </q-item-section>

                    <q-item-section>
                      <q-item-label>{{reference.name}}</q-item-label>
                      <q-item-label subtitle2>{{reference.position}}</q-item-label>
                    </q-item-section>

                    <q-item-section side>
                      <div>
                        <q-btn
                          flat
                          stack
                          type="a"
                          target="_blank"
                          :icon="reference.linkIcon"
                          size="md"
                          color="primary"
                          :href="reference.link"
                        />
                        <q-btn
                          flat
                          stack
                          type="a"
                          target="_blank"
                          icon="mail"
                          size="md"
                          color="primary"
                          :href="`mailto:${reference.email}`"
                        />
                      </div>
                    </q-item-section>

                  </q-item>
                </q-list>
              </q-card-actions>

              <q-card-actions>
                <q-btn
                  outline
                  no-caps
                  label="Website"
                  icon="language"
                  class="fit"
                  type="a"
                  target="_blank"
                  :href="experience.link"
                />
              </q-card-actions>
            </q-card>
          </q-expansion-item>

          <q-separator />
        </q-list>

      </q-card>

      <q-card square id="projects" class="q-ma-md col-md-6 col-xs-11 shadow-5">
        <q-card-section class="q-pa-xs q-ma-none bg-primary text-white">
          <div class="row justify-around">
            <div class="col-12">
              <q-btn
                flat
                dense
                no-caps
                :ripple="false"
                class="text-h6 text-center fit"
                label="Projects"
                @click="updateProjectsState"
              />
            </div>
          </div>
        </q-card-section>
        <q-list
          bordered
          class="fit"
          v-for="(project, idx) in projects"
          :key="idx"
        >
          <q-expansion-item default-opened :value="project.state">
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
            <q-card>
              <q-card-section class="q-pa-sm">
                <div class="fit q-px-md bg-primary rounded-borders text-white text-h6">Description</div>
              </q-card-section>
              <q-card-section class="q-pa-sm">
                <div class="fit q-px-md bg-primary rounded-borders text-white text-h6">Languages, Frameworks, Services, API's</div>
                <div>
                  <q-chip
                    v-for="(item, idx) in project.stack"
                    :key="idx"
                    text-color="white"
                    :label="item.label"
                    :color="item.color"
                    :icon="item.icon"
                  />
                </div>
              </q-card-section>
              <q-card-section class="q-pa-sm">
                <div class="fit q-px-md bg-primary rounded-borders text-white text-h6">Demo & Screenshots</div>
              </q-card-section>

              <q-card-actions>
                <div class="row fit justify-center">
                  <div
                    v-for="(button, idx) in project.buttons"
                    :key="idx"
                    class="q-mx-xs col-xs-12 col-sm-12 col-md-3 col-lg-3 col-xl-3"
                  >
                    <q-btn
                      outline
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
              </q-card-actions>
            </q-card>
            </q-expansion-item>
            <q-separator />
          </q-list>
      </q-card>

      <div class="q-mb-md col-md-6 col-xs-11">
        <q-btn
          outline
          no-caps
          type="a"
          class="fit bg-primary text-white text-center"
          target="_blank"
          icon="ion-logo-github"
          href="https://github.com/flunkout-dvlpr/resume"
          label="Explore This Repo!"
        />
      </div>

    </div>
  </q-page>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      textPlaceHolder: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quidem, eius reprehenderit eos corrupti commodi magni quaerat ex numquam, dolorum officiis modi facere maiores architecto suscipit iste eveniet doloribus ullam aliquid.',
      experiences: [
        {
          companyName: 'Moneta',
          period: '02/2021 - Present',
          title: 'Lead Developer',
          logo: 'https://f6s-public.s3.amazonaws.com/profiles/2616528_th1.jpg',
          icon: null,
          iconBackgroundColor: null,
          description: "Moneta is a fintech service which allows merchants to collect cash and digitally issue any spare change owed to it's customers. As a web application we have two different entries; one for merchants and the other for customers. The merchants access Moneta by making a profile on our website which connects directly to the POS device. When a customer wishes to digitally receive their spare change, the merchant will manually input the change amount and the customers phone number on the Moneta device. The customer will than receive a text message with a link to claim the spare change funds. Simply after creating an account the user can transfer the total collected funds to their bank account of choice. Eventually we plan on having other cash out options like bank-free debit cards or other e-wallets such as Cash App, Venmo, PayPal, etc... It's our mission to become the third party service that on-boards cash users for all digital wallets.",
          link: 'https://www.f6s.com/monetatech',
          references: [
            {
              name: 'Alejandro Alvarez',
              profileImage: 'https://media-exp1.licdn.com/dms/image/C4E03AQGW3EM1DwPyVg/profile-displayphoto-shrink_400_400/0/1582297109037?e=1624492800&v=beta&t=oxQT50K0NcHl_8HBKcfqyBaFwfN0yDkSLIZRVIHSOr0',
              position: 'CEO',
              email: 'alejandro@monetaapp.com',
              link: 'https://www.linkedin.com/in/aaalvarez98/',
              linkIcon: 'ion-logo-linkedin'
            },
            {
              name: 'Quentin Wheeler',
              profileImage: 'https://media-exp1.licdn.com/dms/image/C4E03AQEQKfrg_RXilQ/profile-displayphoto-shrink_400_400/0/1593410035416?e=1624492800&v=beta&t=tf-mfGE0_DMjNV85zjuaWTTiwZHR-2Di_I9PcP1xVjo',
              position: 'COO',
              email: 'quentinw@monetaapp.com',
              link: 'https://www.linkedin.com/in/qwheeler/',
              linkIcon: 'ion-logo-linkedin'
            },
            {
              name: 'Miles Dotson',
              profileImage: 'https://media-exp1.licdn.com/dms/image/C4D03AQH2PEWgsZcnXA/profile-displayphoto-shrink_400_400/0/1516825214390?e=1624492800&v=beta&t=ytVc3JfjFizEXIPCDJtURpbioFfE1L_laZtv9p0lRSM',
              position: 'Devland Advisor',
              email: 'miles@devland.us',
              link: 'https://www.linkedin.com/in/milesdotson',
              linkIcon: 'ion-logo-linkedin'
            },
            {
              name: 'Devon Fanfair',
              profileImage: 'https://media-exp1.licdn.com/dms/image/C4E03AQGZ9tP_9-PQbg/profile-displayphoto-shrink_200_200/0/1614753003234?e=1624492800&v=beta&t=xj4t1sZhrkcD8b9igOT7Pl2a7h-NNq6Y2RFD7uYFp8g',
              position: 'Devland Advisor',
              email: 'devon@devland.us',
              link: 'https://www.linkedin.com/in/devon-fanfair-94b7b524',
              linkIcon: 'ion-logo-linkedin'
            }
          ],
          state: false
        },
        {
          companyName: 'LaunchIt Studio',
          period: '06/2020 - Present',
          title: 'Founder',
          description: '',
          logo: null,
          icon: 'ion-rocket',
          iconBackgroundColor: 'launchit-gradient',
          link: 'http://launchit.studio',
          references: [
            {
              name: 'Me',
              profileImage: 'https://media-exp1.licdn.com/dms/image/C4E03AQH06TWHQ2tZ_w/profile-displayphoto-shrink_400_400/0/1565450126632?e=1624492800&v=beta&t=M2kv1H-Qewc0ZOzBPBHdewWQPxVf8E9PFNBxQc6IoHQ',
              position: 'Founder & CEO',
              email: 'julio@launchit.studio',
              link: 'https://www.linkedin.com/in/julio-gonzalez-4b2904b0',
              linkIcon: 'ion-logo-linkedin'
            }
          ],
          state: false
        },
        {
          companyName: 'Blown Assignments',
          period: '01/2020 - 09/2020',
          title: 'Lead Developer',
          description: 'Blown Assignments is an app that elevates the relationship between coaches and athletes by using accountability and effective communication. Coaches can give athletes the direction they need to reach 100% of their potential through commitment and discipline. Athletes are given directions from their coach to set core athletic goals and develop a winner’s state of mind.',
          role: 'I was recruited to Blown Assignments with the goal of developing a web application based on an existing IOS app, after user feedback suggested a cross platform option was more suitable',
          logo: 'https://f6s-public.s3.amazonaws.com/profiles/2631997_th1.jpg',
          icon: null,
          iconBackgroundColor: null,
          link: 'https://blownassignments.com/home/',
          references: [
            {
              name: 'Paul van der Maas',
              profileImage: 'https://avatars.githubusercontent.com/u/2147175?v=4',
              position: 'Project Manager - Sr. Developer',
              email: 'paul@blownassignments.com',
              link: 'https://github.com/PaulMaas',
              linkIcon: 'ion-logo-github'
            }
          ],
          state: false
        },
        {
          companyName: 'Tech USI',
          period: '01/2018 - 03/2020',
          title: 'Lead Developer',
          description: 'USI leverages a streamlined and automated work-flow driven by full-field CMG simulations to generate physics-based type curves for primary and infill wells in unconventional reservoirs. The Science-Based Forecaster (SBF) software uses reservoir, completion, production and pressure data to quickly reveal solutions for widespread industry challenges',
          role: 'I was with USI since day 1 and helped it go from concept to market. At USI ',
          logo: 'https://media-exp1.licdn.com/dms/image/C560BAQEQUN5csIG6zw/company-logo_100_100/0/1519910264987?e=1626912000&v=beta&t=EH_1x6qvHdi5YqVoq1HRB3Bq6yyzcV1Z6wV3A5k6E1Y',
          icon: null,
          iconBackgroundColor: null,
          link: 'https://www.techusi.com/',
          references: [
            {
              name: 'Duc Lam',
              profileImage: 'https://media-exp1.licdn.com/dms/image/C4E03AQGuXel4ObOqyA/profile-displayphoto-shrink_200_200/0/1596560759185?e=1624492800&v=beta&t=u91BzPb7PaJLYJUIbYzhQ1DyXNhTY3SgSWVE88RBMZw',
              position: 'Founder & CEO',
              email: 'duclam@techusi.com',
              link: 'https://www.linkedin.com/in/duc-lam-p-e-8853932a',
              linkIcon: 'ion-logo-linkedin'
            }
          ],
          state: false
        }
      ],
      projects: [
        {
          name: 'Resume Builder',
          tagline: 'Stand out amongst all other applicants',
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
              color: 'orange',
              icon: 'dns'
            },
            {
              label: 'AWS Code Pipeline',
              color: 'orange',
              icon: 'dns'
            },
            {
              label: 'AWS Route 53',
              color: 'orange',
              icon: 'dns'
            },
            {
              label: 'AWS Code Commit',
              color: 'orange',
              icon: 'dns'
            },
            {
              label: 'AWS Code Build',
              color: 'orange',
              icon: 'dns'
            },
            {
              label: 'AWS Code Deploy',
              color: 'orange',
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
          icon: 'queue_music',
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
              label: 'Frontend Repo',
              icon: 'ion-logo-github',
              link: 'https://github.com/flunkout-dvlpr/barz-bot-frontend'
            },
            {
              label: 'Backend Repo',
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
          icon: 'alarm',
          iconBackgroundColor: 'jarvis-gradient',
          stack: [
            {
              label: 'Vue.js',
              color: 'green',
              icon: 'code'
            }
          ],
          buttons: [
            {
              label: 'Service Repo',
              icon: 'ion-logo-github',
              link: 'https://github.com/flunkout-dvlpr/jarvis'
            }
          ],
          state: false
        },
        {
          name: 'Just Wipes Companion App',
          tagline: '',
          icon: 'sanitizer',
          iconBackgroundColor: 'justwipes-gradient',
          stack: [
            {
              label: 'Vue.js',
              color: 'green',
              icon: 'code'
            }
          ],
          buttons: [
            {
              label: 'Frontend Repo',
              icon: 'ion-logo-github',
              link: 'https://github.com/flunkout-dvlpr/just-wipes-webapp-frontend'
            },
            {
              label: 'Backend Repo',
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
          icon: 'smart_toy',
          iconBackgroundColor: 'bg-orange',
          stack: [
            {
              label: 'Vue.js',
              color: 'green',
              icon: 'code'
            }
          ],
          buttons: [
            {
              label: 'Service Repo',
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
              label: 'Service Repo',
              icon: 'ion-logo-github',
              link: 'https://github.com/flunkout-dvlpr/spotify-remote'
            }
          ],
          state: false
        }
      ]
    }
  },
  methods: {
    updateProjectsState () {
      const currentState = this.projects[0].state
      this.projects.forEach(project => {
        if (currentState) {
          project.state = false
        } else {
          project.state = true
        }
      })
    },
    updateExperiencesState () {
      const currentState = this.experiences[0].state
      this.experiences.forEach(experience => {
        if (currentState) {
          experience.state = false
        } else {
          experience.state = true
        }
      })
    }
  }
}
</script>
