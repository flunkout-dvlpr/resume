<template>
  <q-page>
    <div class="row justify-center items-center content-center">
      <q-card class="q-ma-md col-md-6 col-xs-11 shadow-5">
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

      <q-card class="q-ma-md col-md-6 col-xs-11 shadow-5">
        <q-card-section class="q-pa-xs q-ma-none bg-primary text-white">
          <div class="row justify-around">
            <div class="col-12 text-h6 text-center">
              Experience
            </div>
          </div>
        </q-card-section>
        <q-list
          bordered
          class="fit"
          v-for="(experience, idx) in experiences"
          :key="idx"
        >
          <q-expansion-item default-opened>
            <template v-slot:header>
              <q-item-section avatar>
                <q-avatar size="xl" v-if="experience.logo">
                  <img :src="experience.logo">
                </q-avatar>
                <q-avatar
                  v-else
                  :color="experience.iconBackgroundColor"
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
                <div class="fit q-px-md bg-primary rounded-borders text-white text-h6">About</div>
                <div class="q-pa-sm bg-accent rounded-borders">{{experience.description}}</div>
              </q-card-section>
              <q-card-section class="q-pa-sm">
                <div class="fit q-px-md bg-primary rounded-borders text-white text-h6">Role</div>
                <div class="q-pa-sm bg-accent rounded-borders">{{experience.role}}</div>
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
      <div class="q-mb-md col-md-6 col-xs-11 text-center">
        <q-btn
          outline
          no-caps
          type="a"
          class="fit"
          target="_blank"
          icon="ion-logo-github"
          href="https://github.com/flunkout-dvlpr/resume"
          label="Visit The Repo!"
        />
      </div>

<!--       <q-card class="q-ma-md col-md-6 col-xs-10 shadow-5">
        <q-card-section class="q-pa-xs q-ma-none bg-primary text-white">
          <div class="row justify-around">
            <div class="col-12 text-h6 text-center">
              Projects
            </div>
          </div>
        </q-card-section>
        <q-card-section class="q-pa-xs q-ma-xs">
          <div class="row justify-around">
            <div class="col-12">
              BarzBot Project Name / Link / Date
            </div>
          </div>
          <div class="row justify-around">
            <div class="col-12">
              Description
            </div>
          </div>
        </q-card-section>
        <q-card-section class="q-pa-xs q-ma-xs">
          <div class="row justify-around">
            <div class="col-12">
              Jarvis Project Name / Link / Date
            </div>
          </div>
          <div class="row justify-around">
            <div class="col-12">
             Description
            </div>
          </div>
        </q-card-section>
        <q-card-section class="q-pa-xs q-ma-xs">
          <div class="row justify-around">
            <div class="col-12">
              Just Wipes Project Name / Link / Date
            </div>
          </div>
          <div class="row justify-around">
            <div class="col-12">
             Description
            </div>
          </div>
        </q-card-section>
        <q-card-section class="q-pa-xs q-ma-xs">
          <div class="row justify-around">
            <div class="col-12">
              Twitter Bot Project Name / Link / Date
            </div>
          </div>
          <div class="row justify-around">
            <div class="col-12">
             Description
            </div>
          </div>
        </q-card-section>

      </q-card> -->

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
          ]
        },
        {
          companyName: 'LaunchIt Studio',
          period: '06/2020 - Present',
          title: 'Founder',
          description: '',
          logo: null,
          icon: 'ion-rocket',
          iconBackgroundColor: 'orange',
          link: 'http://launchit.studio',
          references: [
            {
              name: 'Me',
              profileImage: 'https://media-exp1.licdn.com/dms/image/C4E03AQH06TWHQ2tZ_w/profile-displayphoto-shrink_400_400/0/1565450126632?e=1624492800&v=beta&t=M2kv1H-Qewc0ZOzBPBHdewWQPxVf8E9PFNBxQc6IoHQ',
              position: 'Founder & CEO',
              email: 'info@juliogonzalez.space',
              link: 'https://www.linkedin.com/in/julio-gonzalez-4b2904b0',
              linkIcon: 'ion-logo-linkedin'
            }
          ]
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
          ]
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
          ]
        }
      ]
    }
  }
}
</script>
