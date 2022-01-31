<template>
  <q-card square class="fit q-pa-none q-mt-none shadow-5">
    <q-card-section class="q-pa-none q-ma-none launchit-gradient">
      <div class="row justify-center items-center content-center">
        <div class="col-11">
          <div class="text-h6 text-center text-secondary">About Me</div>
        </div>
      </div>
    </q-card-section>
    <q-card-section
      class="q-pa-none q-ma-none bg-secondary"
      style="max-height: 225px;overflow: auto !important"
    >
      <div class="row justify-center items-center content-center">
        <div class="col-11 text-h8 text-left text-black q-px-xs q-pt-md">
          <p v-html="profileBio"/>
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
      profileBio: 'Any given afternoon you can find me at a local coffee shop hacking away at my next project. From automation scripts, web apps, all the way to a Raspberry Pi 3 powered stock ticker, my passion for creating has no limit!.<br>While embarking on a new project is always exciting, experience has thought me that, it is in the process of doing, in which we develop an appreciation for deep understanding, despite the challenges or results.<br>This lesson has also translated into other aspects of my career and overall life, from taking the appropriate time to assess, implement and maintain the habits and routines in my everyday ‘process’ even when challenged or when progress seems impossible.<br>Designing and developing solutions, is much more about our will and commitment to breakdown processes than the efficiency or complexity of the solution itself!<br>Stay Hungry, Stay Foolish'
    }
  }
})
</script>
