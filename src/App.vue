<template>
  <app-header></app-header>
        <div class="container">
            <validateForm></validateForm>
        </div>
    <app-footer></app-footer>
</template>

<script>
  import validateForm from './components/validate';

  export default{
    components:{
      validateForm
    }
  }
</script>
