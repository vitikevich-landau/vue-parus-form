<template>
  <md-app md-mode="reveal">
    <md-app-toolbar class="md-primary ">
      <md-button class="md-icon-button">
        <md-icon>menu</md-icon>
      </md-button>
      <span class="md-title">FORMS.PURUSALTAI.RU</span>
      <md-switch v-model="switchForm"></md-switch>
    </md-app-toolbar>
  </md-app>
</template>

<script>
  export default {
    name: "Header",
    data: () => ({
      switchForm: false
    })
  }
</script>

<style scoped>
  /*@media (max-width: 960px) {*/
  .md-toolbar, .md-toolbar-row {
    min-height: 64px;
    /*min-height: 100%;*/
  }

  /*}*/
  .md-title {
    font-size: 16px;
    margin-left: .1rem !important;
  }
  .md-switch {
    position: absolute;
    right: 2.5%;
  }
</style>
