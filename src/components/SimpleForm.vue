<template>

  <!-- Form -->
  <div class="md-layout">
    <div class="md-layout-item">
      <form novalidate class="md-layout" @submit.prevent="">
        <md-card class="md-layout-item md-size-40 md-large-size-50 md-medium-size-60 md-small-size-100 center">
          <md-card-header>
            <div class="md-title">Users: {{form.phone}}, {{form.company}}</div>
          </md-card-header>

          <md-card-content>
            <div class="">
              <div class="md-layout-item md-small-size-100">
                <md-field>
                  <label for="phone">Номер телефона</label>
                  <md-input
                      v-mask="'+7 (###) ### ####'"
                      placeholder="+7 (___) ___ ____"
                      name="phone"
                      id="phone"
                      autocomplete="off"
                      :value="form.phone"
                      @input="setPhone"
                  />
                </md-field>
              </div>

              <div class="md-layout-item md-small-size-100">
                <md-field>
                  <label for="company">Организация</label>
                  <md-select id="company" v-model="form.company" name="company">
                    <md-option value="australia" selected>Australia</md-option>
                    <md-option value="brazil">Brazil</md-option>
                    <md-option value="japan">Japan</md-option>
                    <md-option value="united-states">United States</md-option>
                  </md-select>
                </md-field>
              </div>
            </div>


          </md-card-content>

<!--          <md-progress-bar md-mode="indeterminate"/>-->

          <md-card-actions class="md-alignment-left">
            <md-button class="md-raised md-primary">Send</md-button>
          </md-card-actions>
          <br>
        </md-card>

<!--        <md-snackbar>The user was saved with success!</md-snackbar>-->
      </form>
    </div>
  </div>

</template>

<script>
  import {validationMixin} from 'vuelidate'
  import {mask} from 'vue-the-mask'

  export default {
    name: 'FormValidation',
    directives: {mask},
    mixins: [validationMixin],
    data: () => ({
      form: {
        phone: null,
        name: null,
        company: 'australia',
        text: null
      },
      phoneFilled: false,
    }),
    validations: {
    },
    methods: {
      setPhone(v) {
        this.form.phone = v;
        /***
         *   Если запрос уже был отправлен, повторно не отправляем
         *
         *   Можно оптимизировать, если предыдущий запрос был с тем же значением,
         *   запрос не отправляем
         * */
        if (!this.phoneFilled && v.length === 17) {
          this.phoneFilled = true;

          if (this.phoneFilled) {
            /***
             *  Send request to server
             */
            console.log('send request to server...');

          }
        } else if (v.length < 17) {
          this.phoneFilled = false;
        }

        console.log(v, v.length, this.phoneFilled);
      }
    }
  }
</script>

<style lang="css" scoped>
  .md-progress-bar {
    position: absolute;
    top: 0;
    right: 0;
    left: 0;
  }

  .center {
    margin: 0 auto;
  }

</style>
