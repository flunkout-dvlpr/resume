<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar class="q-ma-xs row justify-center">
        <div class="col-12 justify-center">
            <div class="row justify-center">
              <img
                :src="profileImage"
                style="width: 125px; height: 125px; border-radius: 50%; border: 5px solid #a1a1a1;"
              >
            </div>
            <div class="row justify-center text-h6">Julio C. Gonzalez</div>
            <div class="row justify-center text-subtiitle1">Full Stack Software Developer</div>
            <div class="row justify-center text-caption">Houston, TX</div>
        </div>
      </q-toolbar>

      <q-tabs
        dense
        class="bg-secondary text-black">
        <q-route-tab to="/page1" no-caps label="About Me" />
        <q-route-tab to="/page2" no-caps label="Experience" />
        <q-route-tab to="/page3" no-caps label="Projects" />
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
      profileImage: 'https://media-exp1.licdn.com/dms/image/C4E03AQH06TWHQ2tZ_w/profile-displayphoto-shrink_400_400/0/1565450126632?e=1624492800&v=beta&t=M2kv1H-Qewc0ZOzBPBHdewWQPxVf8E9PFNBxQc6IoHQ'
    }
  }
}
</script>
