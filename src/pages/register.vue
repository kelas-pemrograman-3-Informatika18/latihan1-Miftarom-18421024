<template>
 <q-page
 class="window-height window-width row justify-center items-center"
    style="background: linear-gradient(#FFFFFF, #FFFFFF);">
      <q-form
      @submit="onSubmit"
      @reset="onReset"
      class="q-gutter-md"
    >
    <p v-if="showMessage"> {{message}}</p>
    <div>
      <q-input
        filled
        v-model="Nama"
        label="Full Name *"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Please type your name']"
        :dense="dense"
      />

      <q-input
        filled
        v-model="username"
        label="Your username *"
        :rules="[ val => val !== null && val.length <= 12 || 'Please type username Max 12 char']"
        :dense="dense"
      />

      <q-input
        filled
        type="password"
        v-model="password"
        label="Your password *"
        :rules="[val => val !== null && val.length >= 0 || 'Please type your password Max 12 char',
        ]"
        :dense="dense"
      />

      <q-input
        filled
        type="password"
        v-model="password1"
        label="re-type password *"
        :rules="[
          val => val !== null && val.length >= 0 || 'Please re-type your password Max 12 char',
        ]"
        :dense="dense"
      />
      <q-input v-model="date" filled type="date" hint="date of birth" :dense="dense" />

      <div class="q-pa-md q-gutter-sm">
        <div class="q-gutter-sm">
          <q-radio dense v-model="gender" val="male" label="Male" />
          <q-radio dense v-model="gender" val="female" label="Female" />
        </div>
        <div class="q-px-sm q-pt-sm">
          Your selection is: <strong>{{ gender }}</strong>
        </div>
      </div>
      <q-input
        filled
        v-model="Address"
        autogrow
        label="Your Address *"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Please type your Address']"
      />
    </div>
      <div>
        <q-btn to="/" label="Register" type="submit"
        :loading="submitting" color="primary"/>
        <q-btn label="reset" type="reset" color="primary" flat class="q-ml-sm" />
        <q-btn to="/" label="back" type="back" color="primary" flat class="q-ml-sm" />
      </div>
    </q-form>
 </q-page>
</template>
<script>
export default {
  data () {
    return {
      message: 'Register Page',
      showMessage: true,
      username: null,
      password: null,
      password1: null,
      gender: null,
      Nama: null,
      Address: null,
      date: null,
      submitting: false,
      dense: true
    }
  },
  methods: {
    onSubmit () {
      this.submitting = true
      setTimeout(() => {
        // delay simulated, we are done,
        // now restoring submit to its initial state
        this.submitting = false
      }, 3000)
    },
    onReset () {
      this.username = null
      this.password = null
      this.password1 = null
      this.date = null
      this.Nama = null
      this.Address = null
      this.gender = null
    }
  }
}
</script>
