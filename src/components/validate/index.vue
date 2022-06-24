<!-- vee-validate with yup -->

<template>

    <Form @submit="onSubmit" :validation-schema="formSchema">

        <div class="form-group">
            <label for="name">Name</label>
            <Field 
                name="name" 
                
                placeholder="Enter your name"
                class="form-control"
            />
            <ErrorMessage name="name" as="div" v-slot="{ message }">
                <div class="alert alert-danger" role="alert">
                    {{ message }}
                </div>
            </ErrorMessage>
        </div>


        <div class="form-group">
            <label for="email">Email</label>
            <Field name="email"  v-slot="{field, errors }">

                <input
                    type="text"
                    id="email"
                    class="form-control"
                    v-bind="field"
                    :class="{'is-invalid': errors.length !== 0}"
                />
            </Field>


        </div>
 <div class="form-group">
            <label for="message">Message</label>
            <Field name="message" v-slot="{ field, errors, errorMessage }">

                <textarea
                    class="form-control"
                    :class="{'is-invalid': errors.length !== 0}"
                    id="message"
                    rows="3"
                    v-bind="field"
                ></textarea>
                <div 
                    class="alert alert-danger" 
                    role="alert"
                    v-if="errors.length !== 0"
                >
                    {{ errorMessage }}
                </div>

            </Field>
        </div>

    
        <hr/>
        <button
          class="btn btn-primary"
        >
          Submit
        </button>

    </Form>

</template>

<script>
    import { Field, Form, ErrorMessage } from 'vee-validate'
        import * as yup from 'yup';
    export default {
        components:{
            Field,
            Form,
            ErrorMessage
        },
        data(){
            return {
                formSchema:{
                    name:yup.string().required('The name is required'),
                    email:yup.string().required('The email is required').email('Not a valid email'),
                    message:yup.string().required('The message is required')
                }
            }
        },
        methods:{
           onSubmit(values,{ resetForm }){
                console.log(values)
                resetForm();
            } 
        }
    }
</script>

