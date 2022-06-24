<template>
  <form @submit="checkForm">
    <div class="row">
      <div class="col-xl-12">
        <h1>Contact us</h1>
        <hr />

        <div class="form-group">
          <label for="name">Name</label>
          <input type="text" id="name" v-model="formData.name" class="form-control" />
        </div>

        <div class="form-group">
          <label for="email">email</label>
          <input type="email" id="email" v-model = "formData.email" class="form-control" />
        </div>

        <div class="form-group">
          <label for="subject">Subject</label>
          <input type="text" v-model = "formData.subject" id="subject" class="form-control" />
        </div>

        <div class="form-group">
          <label for="message">Message</label>
          <textarea class="form-control" v-model = "formData.message" rows="3" id="message"></textarea>
        </div>


        <div class="form-group">
          <h5>Want more spam ? </h5>
          <div class="form-check">
            <input class="form-check-input" v-model = "formData.spam" type="checkbox" value="Newsletter" id="newsletter">
            <label class="form-check-label" for="newsletter">
              Newsletter
            </label>
          </div>
          <div class="form-check">
            <input class="form-check-input" v-model = "formData.spam" type="checkbox" value="Promotions" id="promotions">
            <label class="form-check-label" for="newsletter">
              Promotions
            </label>
          </div>
        </div>

        <div class="form-group">
          <h5>What are you ? </h5>
          <div class="form-check">
            <input class="form-check-input" type="radio"  v-model = "formData.gender" id="human" value="human" name="origin">
            <label class="form-check-label" for="human">
              Human
            </label>
          </div>
          <div class="form-check">
            <input class="form-check-input" type="radio"  v-model = "formData.gender" id="alien" value="alien" name="origin">
            <label class="form-check-label" for="alien">
              Alien
            </label>
          </div>
        </div>

        <div class="form-group">
          <label for="country">Country</label>
          <select class="form-control" id="country" v-model ="formData.country">
            <option  v-for="(country, index) in countries"
              :key="index+country">
            {{ country }}
            </option>
          </select>
        </div>


      </div>
    </div>
    <div class="form-group">

      <button  class="btn btn-primary">submit</button>
    </div>
  </form>
  <p v-if="this.errors.length">
            <b>Ooops, fix the errors:</b>
            <ul>
              <li v-for="error in errors" :key="error">
                {{ error }}
              </li>
            </ul>
        </p>
</template>
<script>
export default {
  data() {
    return {
          errors:[],
      countries : ['a','b','c'],
      formData: {
        name: '',
        email: '',
        message: '',
        subject :'',
        spam :[],
        gender : 'human',
        country : ''

      }

    }
  },
  methods: {
    checkForm(e){
        e.preventDefault();
        this.errors = [];
        if(!this.formData.name){
          this.errors.push('Sorry, the name is required')
        }
        if(!this.formData.email){
          this.errors.push('Sorry, the email is required')
        } else if(!this.validEmail(this.email)){
          this.errors.push('Sorry, the email is not valid')
        }
        if(!this.errors.length){
          this.submitForm()
        }
      },
    submitForm() {
      console.log(JSON.stringify(this.formData))
    }
  },
   validEmail(email){
        const re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
        return re.test(email);
      }
}
</script>
