<template>
   <b-card>
    <form-wizard
      color="#4D44B5"
      :title="null"
      :subtitle="null"
      shape="circle"
      finish-button-text="Submit"
      back-button-text="السابق"
      next-button-text="التالي"
      class="mb-3"
      @on-complete="formSubmitted"
    >

      <!-- accoint details tab -->
      <tab-content
        title="السنة الدراسية"
        :before-change="validationForm"
      >
        <year-step/>
      </tab-content>

      <!-- personal details tab -->
      <tab-content
        title="التخصص"
        :before-change="validationFormInfo"
      >
       
      </tab-content>

      <!-- address  -->
      <tab-content
        title="المقرر الدراسي"
        :before-change="validationFormAddress"
      >
        
      </tab-content>

      <!-- social link -->
      <tab-content
        title="تفاصيل الإختبار"
        :before-change="validationFormSocial"
      >
     
      </tab-content>

      <tab-content
        title="نشر الإختبار"
        :before-change="validationFormSocial"
      >
     
      </tab-content>
    </form-wizard>

  </b-card>
</template>

<script>
import { FormWizard, TabContent } from 'vue-form-wizard'
import { BCard } from 'bootstrap-vue'
import vSelect from 'vue-select'
import { ValidationProvider, ValidationObserver } from 'vee-validate'
import ToastificationContent from '@core/components/toastification/ToastificationContent.vue'
import 'vue-form-wizard/dist/vue-form-wizard.min.css'
import {
  BRow,
  BCol,
  BFormGroup,
  BFormInput,
  BFormInvalidFeedback,
  
} from 'bootstrap-vue'
import { required, email } from '@validations'
import  YearStep  from './components/YearStep.vue'

export default {
  components: {
    ValidationProvider,
    ValidationObserver,
    FormWizard,
    TabContent,
    BRow,
    BCol,
    BCard,
    BFormGroup,
    BFormInput,
    vSelect,
    YearStep,
    BFormInvalidFeedback,
    // eslint-disable-next-line vue/no-unused-components
    ToastificationContent,
  },
  data() {
    return {
      selectedContry: '',
      selectedLanguage: '',
      name: '',
      emailValue: '',
      PasswordValue: '',
      passwordCon: '',
      first_name: '',
      last_name: '',
      address: '',
      landMark: '',
      pincode: '',
      twitterUrl: '',
      facebookUrl: '',
      googleUrl: '',
      linkedinUrl: '',
      city: '',
      required,
      email,
      countryName: [
        { value: 'select_value', text: 'Select Value' },
        { value: 'Russia', text: 'Russia' },
        { value: 'Canada', text: 'Canada' },
        { value: 'China', text: 'China' },
        { value: 'United States', text: 'United States' },
        { value: 'Brazil', text: 'Brazil' },
        { value: 'Australia', text: 'Australia' },
        { value: 'India', text: 'India' },
      ],
      languageName: [
        { value: 'nothing_selected', text: 'Nothing Selected' },
        { value: 'English', text: 'English' },
        { value: 'Chinese', text: 'Mandarin Chinese' },
        { value: 'Hindi', text: 'Hindi' },
        { value: 'Spanish', text: 'Spanish' },
        { value: 'Arabic', text: 'Arabic' },
        { value: 'Malay', text: 'Malay' },
        { value: 'Russian', text: 'Russian' },
      ],
    }
  },
  methods: {
    formSubmitted() {
      this.$toast({
        component: ToastificationContent,
        props: {
          title: 'Form Submitted',
          icon: 'EditIcon',
          variant: 'success',
        },
      })
    },
    validationForm() {
      return new Promise((resolve, reject) => {
        this.$refs.accountRules.validate().then(success => {
          if (success) {
            resolve(true)
          } else {
            reject()
          }
        })
      })
    },
    validationFormInfo() {
      return new Promise((resolve, reject) => {
        this.$refs.infoRules.validate().then(success => {
          if (success) {
            resolve(true)
          } else {
            reject()
          }
        })
      })
    },
    validationFormAddress() {
      return new Promise((resolve, reject) => {
        this.$refs.addressRules.validate().then(success => {
          if (success) {
            resolve(true)
          } else {
            reject()
          }
        })
      })
    },
    validationFormSocial() {
      return new Promise((resolve, reject) => {
        this.$refs.socialRules.validate().then(success => {
          if (success) {
            resolve(true)
          } else {
            reject()
          }
        })
      })
    },
  },
}
</script>
<style>
.vue-form-wizard .wizard-btn{
  border-radius: 65px;
}
.vue-form-wizard.md .wizard-icon-circle {
  width: 51px;
  height: 51px;
  font-size: 18px;
}
.vue-form-wizard .wizard-icon-circle {
  border: 1px solid #A098AE;
  border-radius: 50%;
}
.vue-form-wizard .wizard-nav-pills > li > a {
  color: #A098AE;
}
.vue-form-wizard .wizard-icon-circle .wizard-icon{
  font-style: normal;
  font-weight: 100;
}
</style>
