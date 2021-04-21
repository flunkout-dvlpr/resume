<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar class="q-ma-xs row justify-center">
        <div class="col-12 justify-center">
            <div class="row justify-center text-center text-h4">Julio C. Gonzalez</div>
            <div class="row justify-center text-center text-h10">Software Developer</div>
        </div>
      </q-toolbar>
    </q-header>

    <q-footer elevated>
      <q-toolbar class="q-ma-xs row justify-center">
        <div class="col-xs-3 col-sm-3 col-md-1 col-lg-1 col-xl-1">
          <q-btn
            flat
            class="fit"
            type="a"
            target="_blank"
            icon="ion-logo-github"
            size="lg"
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
            size="lg"
            href="https://www.linkedin.com/in/julio-gonzalez-4b2904b0"
          />
        </div>
        <div class="col-xs-3 col-sm-3 col-md-1 col-lg-1 col-xl-1">
          <q-btn
            flat
            class="fit"
            type="a"
            icon="phone"
            size="lg"
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
            size="lg"
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
  name: 'MainLayout'
}
</script>
