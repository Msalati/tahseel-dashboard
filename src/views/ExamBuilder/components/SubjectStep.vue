<template>
  <div>
    <!-- card 1 -->
    <b-card header="يرجى إختيار المقرر الدراسي">
      <b-card-text>
        في هذه المرحلة من إنشاء إختبار جديد يرجى إختيار المقرر الدراسي المراد
        إنشاء اختبار له وذلك بعد الحرص على إختيار الفصل الدراسي قبل، يمكنك
        اختيار الفصلين معا من خلالا اختيار نهاية السنة الدراسية أو اختيار كل فصل
        على حدا، عندما تنتهي من اخيار الفصل والمقرر المراد إختياره انقر زر
        التالي في الأسفل :
      </b-card-text>
      <b-row>
        <b-col cols="12">
          <label class="label" for="semester">الفصل الدراسي لهذا العام*</label>
          <div class="demo-inline-spacing">
            <b-form-radio v-model="semester" plain name="some-radios" value="A">
              الفصل الأول
            </b-form-radio>
            <b-form-radio v-model="semester" plain name="some-radios" value="B">
              الفصل الثاني
            </b-form-radio>
            <b-form-radio v-model="semester" plain name="some-radios" value="c">
              نهاية السنة الدراسية
            </b-form-radio>
          </div>
        </b-col>
        <b-col cols="12" class="mt-3 business-card">
          <h6 class="mb-75 label">مواد السنة الدراسية</h6>
          <b-row class="business-items">
            <div
              v-for="(subject, index) in subjects"
              :key="index"
              class="business-item col-md-6"
            >
              <div class="d-flex align-items-center justify-content-between">
                <b-form-radio v-model="chosenSubject" name="some-radio9">
                  {{ subject.value }}
                </b-form-radio>
                <b-badge :variant="subject.variant">
                  <feather-icon
                    :icon="subject.icon"
                    size="18"
                    class="cursor-pointer"
                  />
                </b-badge>
              </div>
            </div>
          </b-row>
        </b-col>
      </b-row>
    </b-card>
  </div>
</template>

<script>
import {
  BCard,
  BRow,
  BCol,
  BCardText,
  BButton,
  BFormRadio,
  BFormCheckbox,
  BBadge,
} from "bootstrap-vue";
import Ripple from "vue-ripple-directive";

export default {
  props: {
    subjects: {
      required: true,
      type: Array,
    },
  },
  components: {
    BCard,
    BRow,
    BFormCheckbox,
    BCol,
    BCardText,
    BButton,
    BFormRadio,
    BBadge,
  },
  directives: {
    Ripple,
  },
  data() {
    return {
      chosenSubject: "",
      semester: "",
    };
  },
};
</script>

<style>
.card .card-header {
  background: #4d44b5;
  color: #fff;
  border-radius: 20px 20px 0px 0px;
  font-weight: 400;
  font-size: 24px;
}
.card-text {
  margin-top: 12px;
  font-weight: 400;
  font-size: 14px;
  line-height: 27px;
  /* Color/Gray 3 */
  color: #a098ae;
}
.card .card-img-overlay.bg-overlay {
  background: none;
}
.custom-radio .custom-control-label::before {
  border-radius: 3px;
  border: #a098ae solid 2px;
}
.radio {
  padding: 10px;
  background: #fcfcfc;
  border-radius: 14px;
}
.custom-checkbox .custom-control-label,
.custom-radio .custom-control-label {
  font-size: 16px;
}
.label {
  font-weight: 600;
  font-size: 18px;
  line-height: 27px;

  /* Color/Text */
  color: #303972;
}
</style>