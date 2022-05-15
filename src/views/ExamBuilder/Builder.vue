<template>
  <b-card>
    <form-wizard
      color="#4D44B5"
      :title="null"
      ref="wizard"
      :subtitle="null"
      shape="circle"
      finish-button-text="Submit"
      back-button-text="السابق"
      next-button-text="التالي"
      class="mb-3"
      @on-complete="formSubmitted"
    >
      <!-- accoint details tab -->
      <tab-content title="السنة الدراسية">
        <year-step />
      </tab-content>

      <!-- personal details tab -->
      <tab-content title="التخصص">
        <specialty-step @getValue="getSubjects" />
      </tab-content>

      <!-- address  -->
      <tab-content title="المقرر الدراسي">
        <subject-step :subjects="subjects" />
      </tab-content>

      <!-- social link -->
      <tab-content title="تفاصيل الإختبار">
        <exam-detail-step />
      </tab-content>

      <tab-content title="نشر الإختبار">
      <last-step/>
       </tab-content>

      <template slot="footer">
        <div class="wizard-footer-right">
          <b-button
            v-ripple.400="'rgba(113, 102, 240, 0.15)'"
            variant="outline-primary"
            class="mr-1"
            pill
          >
            حفظ كمسودة
          </b-button>
          <b-button
            @click="nextStep()"
            v-ripple.400="'rgba(113, 102, 240, 0.15)'"
            :variant="isLastStep ? 'success' : 'primary'"
            pill
          >
            {{ isLastStep ? "نشر" : "التالي" }}
          </b-button>
        </div>
      </template></form-wizard
    ></b-card
  >
</template>
    </form-wizard>

  </b-card>
</template>

<script>
import { FormWizard, TabContent } from "vue-form-wizard";
import { BCard, BButton } from "bootstrap-vue";
import vSelect from "vue-select";
import { ValidationProvider, ValidationObserver } from "vee-validate";
import ToastificationContent from "@core/components/toastification/ToastificationContent.vue";
import "vue-form-wizard/dist/vue-form-wizard.min.css";
import Ripple from "vue-ripple-directive";
import {
  BRow,
  BCol,
  BFormGroup,
  BFormInput,
  BFormInvalidFeedback,
} from "bootstrap-vue";
import { required, email } from "@validations";
import YearStep from "./components/YearStep.vue";
import SpecialtyStep from "./components/SpecialtyStep.vue";
import ExamDetailStep from "./components/ExamDetailStep.vue";
import SubjectStep from "./components/SubjectStep.vue";
import LastStep from "./components/LastStep.vue";

export default {
  directives: {
    Ripple,
  },
  components: {
    ValidationProvider,
    ValidationObserver,
    FormWizard,
    TabContent,
    BRow,
    BCol,
    BButton,
    BCard,
    BFormGroup,
    BFormInput,
    vSelect,
    YearStep,
    SpecialtyStep,
    ExamDetailStep,
    SubjectStep,
    BFormInvalidFeedback,
    LastStep,
    // eslint-disable-next-line vue/no-unused-components
    ToastificationContent,
  },
  data() {
    return {
      selectedContry: "",
      isLastStep: false,
      selectedLanguage: "",
      subjects:[]
    };
  },
  methods: {
    formSubmitted() {
      this.$toast({
        component: ToastificationContent,
        props: {
          title: "Form Submitted",
          icon: "EditIcon",
          variant: "success",
        },
      });
    },
    getSubjects(data) {
      this.subjects = data.subjects
    },
    checkLastStep() {
      this.isLastStep = this.$refs.wizard.tabs[4].active;
    },
    nextStep() {
      this.$refs.wizard.nextTab();
      this.checkLastStep();
    },
    validationForm() {
      return new Promise((resolve, reject) => {
        this.$refs.accountRules.validate().then((success) => {
          if (success) {
            resolve(true);
          } else {
            reject();
          }
        });
      });
    },
    validationFormInfo() {
      return new Promise((resolve, reject) => {
        this.$refs.infoRules.validate().then((success) => {
          if (success) {
            resolve(true);
          } else {
            reject();
          }
        });
      });
    },
    validationFormAddress() {
      return new Promise((resolve, reject) => {
        this.$refs.addressRules.validate().then((success) => {
          if (success) {
            resolve(true);
          } else {
            reject();
          }
        });
      });
    },
    validationFormSocial() {
      return new Promise((resolve, reject) => {
        this.$refs.socialRules.validate().then((success) => {
          if (success) {
            resolve(true);
          } else {
            reject();
          }
        });
      });
    },
  },
};
</script>
<style>
.vue-form-wizard .wizard-btn {
  border-radius: 65px;
}
.vue-form-wizard.md .wizard-icon-circle {
  width: 51px;
  height: 51px;
  font-size: 18px;
}
.vue-form-wizard .wizard-icon-circle {
  border: 1px solid #a098ae;
  border-radius: 50%;
}
.vue-form-wizard .wizard-nav-pills > li > a {
  color: #a098ae;
}
.vue-form-wizard .wizard-icon-circle .wizard-icon {
  font-style: normal;
  font-weight: 100;
}
</style>
