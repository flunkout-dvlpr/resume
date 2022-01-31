<template>
  <q-page
    id="scroll-section"
    class="hide-scrollbar bg-primary"
    style="max-height: 350px;overflow: auto !important"
  >
    <div class="row q-pt-sm justify-center items-center content-center">
      <div class="q-py-xs col-md-6 col-xs-11">
        <AboutMe class="scroll-pad" id="about-me"/>
      </div>
    </div>
    <div class="row q-py-sm justify-center items-center content-center">
      <div class="q-py-xs col-md-6 col-xs-11">
        <Experience class="scroll-pad" id="experience"/>
      </div>
    </div>
    <div class="row q-pb-sm justify-center items-center content-center">
      <div class="q-py-xs col-md-6 col-xs-11">
        <Project class="scroll-pad" id="projects"/>
      </div>
<!--       <div class="q-mb-md col-md-6 col-xs-11">
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
      </div> -->
    </div>
  </q-page>
</template>

<script>
import AboutMe from 'components/AboutMe'
import Experience from 'components/Experience'
import Project from 'components/Project'
export default {
  name: 'Home',
  components: {
    AboutMe,
    Experience,
    Project
  },
  data () {
    return {
    }
  },
  methods: {
  }
}
</script>

<style type="text/css">
.scroll-pad {
  scroll-margin-top: 10px;
}
</style>
