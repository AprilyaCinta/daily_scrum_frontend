<template>
    <div class="container-scroller">
    <div class="container-fluid page-body-wrapper full-page-wrapper">
      <div class="main-panel">
        <div class="content-wrapper d-flex align-items-center auth">
          <div class="row w-100">
            <div class="col-lg-4 mx-auto">
              <div class="auth-form-light text-left p-5">
                <div class="navbar-brand brand-logo">
                  <img src="assets/img/logo.svg">
                </div>
                <h4>Selamat datang!</h4>
                <h6 class="font-weight-light">Daftar untuk menggunakan aplikasi daily scrum.</h6>
                <form class="pt-3" v-on:submit.prevent="Register">
                  <div class="form-group">
                    <div class="input-group">
                      <div class="input-group-prepend bg-transparent">
                        <span class="input-group-text bg-transparent border-right-0">
                          <i class="mdi mdi-account-outline text-primary"></i>
                        </span>
                      </div>
                      <input type="text" class="form-control form-control-lg border-left-0" id="input_firstname" name="input_firstname" placeholder="First Name" v-model="firstname" required>
                    </div>
                  </div>
                  <div class="form-group">
                    <div class="input-group">
                      <div class="input-group-prepend bg-transparent">
                        <span class="input-group-text bg-transparent border-right-0">
                          <i class="mdi mdi-account-outline text-primary"></i>
                        </span>
                      </div>
                      <input type="text" class="form-control form-control-lg border-left-0" id="input_lastname" name="input_lastname" placeholder="Last Name" v-model="lastname" required>
                    </div>
                  </div>
                  <div class="form-group">
                    <div class="input-group">
                      <div class="input-group-prepend bg-transparent">
                        <span class="input-group-text bg-transparent border-right-0">
                          <i class="mdi mdi-message-outline text-primary"></i>
                        </span>
                      </div>
                      <input type="email" class="form-control form-control-lg border-left-0" id="input_email" name="input_email" placeholder="E-Mail" v-model="email" required>
                    </div>
                  </div>
                  <div class="form-group">
                    <div class="input-group">
                      <div class="input-group-prepend bg-transparent">
                        <span class="input-group-text bg-transparent border-right-0">
                          <i class="mdi mdi-lock-outline text-primary"></i>
                        </span>
                      </div>
                      <input type="password" class="form-control form-control-lg border-left-0" name="input_password" id="input_password" placeholder="New Password" v-model="password" required>                        
                    </div>
                  </div>
                  <div class="form-group">
                    <div class="input-group">
                      <div class="input-group-prepend bg-transparent">
                        <span class="input-group-text bg-transparent border-right-0">
                          <i class="mdi mdi-lock-outline text-primary"></i>
                        </span>
                      </div>
                      <input type="password" class="form-control form-control-lg border-left-0" name="input_password_verify" id="input_password_verify" placeholder="Retype Your New Password" v-model="password_verify" required>                        
                    </div>
                  </div>
                  <div class="my-3">
                    <input type="submit" href="#pablo" name="register" class="btn btn-block btn-primary btn-lg font-weight-medium auth-form-btn" value="register">
                  </div>
                </form>
              </div>
            </div>
          </div>
        </div>
      </div>
      <!-- content-wrapper ends -->
    </div>
    <!-- page-body-wrapper ends -->
  </div>
</template>

<script>
export default {
    data() {
      return {
        firstname:"",
        lastname:"",
        email: '',
        password: '',
        password_verify: ''
      }
    },
    methods: {
        Register: function(){
            let firstname = this.firstname
            let lastname = this.lastname
            let email = this.email 
            let password = this.password
            let password_verify = this.password_verify
            this.$store.dispatch('register', { firstname, lastname, email, password, password_verify })
            .then(() => this.$router.push('/login'))
            .catch(err => console.log(err))
        }
    }
}
</script>