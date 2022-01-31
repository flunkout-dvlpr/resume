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
            @click="updateExperiencesState"
          >
            <div class="text-h6 text-center text-secondary">
              Experience
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
            v-for="(experience, idx) in experiences"
            :key="idx"
          >
            <!-- Job Logo/Title/Period -->
            <q-expansion-item :default-opened="false" group="projects">
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

              <q-card square>
                <!-- Job Description -->
                <q-card-section class="q-pa-none">
                  <div class="q-px-sm fit bg-primary text-white text-h6">
                    About The Employer
                  </div>
                  <div class="q-pa-md bg-secondary">
                    {{experience.description}}
                  </div>
                </q-card-section>
                <!-- Job Role/Responsibilities -->
                <q-card-section class="q-pa-none">
                  <div class="q-px-md fit bg-primary text-white text-h6">
                    Role & Responsibilities
                  </div>
                  <div class="q-px-lg q-py-sm bg-secondary">
                    {{experience.role}}
                  </div>
                </q-card-section>
                <!-- Job References -->
                <q-card-section class="q-pa-none">
                  <div class="q-px-sm fit bg-primary text-white text-h6">
                    References
                  </div>
                  <q-list
                    bordered
                    class="fit"
                    v-for="(reference, idx) in experience.references"
                    :key="idx"
                  >
                    <q-item
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

                      <q-item-section class="items-end">
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
                </q-card-section>

                <q-card-actions>
                  <q-btn
                    flat
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
        </div>
      </div>
    </q-card-section>
  </q-card>
</template>

<script>
export default ({
  name: 'AboutMe',
  data () {
    return {
      experiences: [
        {
          companyName: 'Moneta',
          period: '01/2021 - Present',
          title: 'CTO',
          logo: 'moneta.png',
          icon: null,
          iconBackgroundColor: null,
          description: "Moneta is a fintech service which allows merchants to collect cash and digitally issue any spare change owed to it's customers. As a web application we have two different entries; one for merchants and the other for customers. The merchants access Moneta by making a profile on our website which connects directly to the POS device. When a customer wishes to digitally receive their spare change, the merchant will manually input the change amount and the customers phone number on the Moneta device. The customer will than receive a text message with a link to claim the spare change funds. Simply after creating an account the user can transfer the total collected funds to their bank account of choice. Eventually we plan on having other cash out options like bank-free debit cards or other e-wallets such as Cash App, Venmo, PayPal, etc... It's our mission to become the third party service that on-boards cash users for all digital wallets.",
          link: 'https://www.monetaapp.com',
          references: [
            {
              name: 'Alejandro Alvarez',
              profileImage: 'https://media-exp1.licdn.com/dms/image/D4E03AQHnrLK2fbf0tA/profile-displayphoto-shrink_400_400/0/1636671444943?e=1648684800&v=beta&t=ZnI0FKP7rGaNRCSr1LhZje0TFEHnYRNhMgeYem8lxBc',
              position: 'CEO',
              email: 'alejandro@monetaapp.com',
              link: 'https://www.linkedin.com/in/aaalvarez98/',
              linkIcon: 'ion-logo-linkedin'
            },
            {
              name: 'Quentin Wheeler',
              profileImage: 'https://media-exp1.licdn.com/dms/image/C4E03AQEQKfrg_RXilQ/profile-displayphoto-shrink_400_400/0/1593410035416?e=1648684800&v=beta&t=hlIGSpdpWY-GJx3nrK6Rtv0B0M166vLWRVaCIu_pIlE',
              position: 'COO',
              email: 'quentinw@monetaapp.com',
              link: 'https://www.linkedin.com/in/qwheeler/',
              linkIcon: 'ion-logo-linkedin'
            },
            {
              name: 'Miles Dotson',
              profileImage: 'https://media-exp1.licdn.com/dms/image/D5603AQGztHplZ5dxgw/profile-displayphoto-shrink_400_400/0/1635716175764?e=1648684800&v=beta&t=TDQlYbIsoIfPisYI4rxG3CGNHaz9bW1wDsS0ym-kTJI',
              position: 'Devland Advisor',
              email: 'miles@devland.us',
              link: 'https://www.linkedin.com/in/milesdotson',
              linkIcon: 'ion-logo-linkedin'
            },
            {
              name: 'Devon Fanfair',
              profileImage: 'https://media-exp1.licdn.com/dms/image/C4E03AQHuA_1cy5XyUw/profile-displayphoto-shrink_400_400/0/1623648302950?e=1648684800&v=beta&t=XV9kND4ZTo-zzPVksnOhBqa_Qfk0r_fksimm66idwaw',
              position: 'Devland Advisor',
              email: 'devon@devland.us',
              link: 'https://www.linkedin.com/in/devon-fanfair-94b7b524',
              linkIcon: 'ion-logo-linkedin'
            }
          ],
          state: false
        },
        // {
        //   companyName: 'LaunchIt Studio',
        //   period: '06/2020 - Present',
        //   title: 'Founder',
        //   description: '',
        //   logo: null,
        //   icon: 'ion-rocket',
        //   iconBackgroundColor: 'launchit-gradient',
        //   link: 'http://launchit.studio',
        //   references: [
        //     {
        //       name: 'Julio Gonzalez',
        //       profileImage: 'profile.jpeg',
        //       position: 'Me',
        //       email: 'julio@launchit.studio',
        //       link: 'https://www.linkedin.com/in/julio-gonzalez-4b2904b0',
        //       linkIcon: 'ion-logo-linkedin'
        //     }
        //   ],
        //   state: false
        // },
        {
          companyName: 'Blown Assignments',
          period: '01/2020 - 12/2020',
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
          period: '01/2018 - 05/2020',
          title: 'Lead Developer',
          description: 'USI leverages a streamlined and automated work-flow driven by full-field CMG simulations to generate physics-based type curves for primary and infill wells in unconventional reservoirs. The Science-Based Forecaster (SBF) software uses reservoir, completion, production and pressure data to quickly reveal solutions for widespread industry challenges',
          role: 'I was with USI since day 1 and helped it go from concept to market. At USI ',
          logo: 'https://media-exp1.licdn.com/dms/image/C560BAQEQUN5csIG6zw/company-logo_100_100/0/1519910264987?e=1651104000&v=beta&t=NTwWaUXZm1Oh63yluV2mba1xLBiRPOVdaog2wKgM1-w',
          icon: null,
          iconBackgroundColor: null,
          link: 'https://www.techusi.com/',
          references: [
            {
              name: 'Duc Lam',
              profileImage: 'https://media-exp1.licdn.com/dms/image/C4E03AQGuXel4ObOqyA/profile-displayphoto-shrink_100_100/0/1596560759185?e=1648684800&v=beta&t=ZGQBjPiUXXZow9JZ3ELltCCsEtLxifx55K9NzxDSEg8',
              position: 'Founder & CEO',
              email: 'duclam@techusi.com',
              link: 'https://www.linkedin.com/in/duc-lam-p-e-8853932a',
              linkIcon: 'ion-logo-linkedin'
            }
          ],
          state: false
        }
      ]
    }
  },
  methods: {
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
})
</script>
