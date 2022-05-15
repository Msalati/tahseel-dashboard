<template>
  <div>
    <!-- card 1 -->
    <b-card header="يرجى تحديد التفاصيل التالية للإختبار">
      <b-row class="mt-3">
        <b-col>
          <b-form-group label="إسم نموذج الإختبار *" label-for="v-first-name">
            <b-form-input
              id="v-first-name"
              placeholder="إختبار نهاية الفصل الأول"
            />
          </b-form-group>

          <b-form-group
            label="تاريخ بدء وإنتهاء الإختبار*"
            label-for="v-first-name"
          >
            <b-form-datepicker
              id="datepicker-placeholder"
              class="mb-1"
              placeholder="تاريخ البداية"
              local="en"
              initial-date="2020-06-16"
            />
            <b-form-datepicker
              id="datepicker-placeholder"
              placeholder="تاريخ النهاية"
              local="en"
              initial-date="2020-06-16"
            />
          </b-form-group>

          <b-row class="mt-4">
            <b-col md="12"
              ><label>كم أقصى موعد يمكن أن يستغرقه الطالب للحل؟ *</label>
            </b-col>
            <b-col md="12" class="d-flex align-items-center custom-time">
              <feather-icon class="text-warning" icon="ClockIcon" size="15" />
              <span class="mr-2">الزمن بالدقائق </span>
              <b-form-input
                placeholder="20"
                class="custom-input-minutes"
              ></b-form-input>
            </b-col>
          </b-row>

          <div class="mt-4">
            <label>مستوى تعقيد الإختبار*</label>
            <div class="diff-buttons">
              <b-button
                class="mt-1 color-primary bg-custom-easy"
                v-ripple.400="'rgba(40, 199, 111, 0.15)'"
                pill
                >سهل
              </b-button>
              <b-button
                class="mt-1 color-primary bg-custom-medium"
                v-ripple.400="'rgba(240, 199, 111, 0.15)'"
                pill
                >متوسط
              </b-button>
              <b-button
                class="mt-1 color-primary bg-custom-hard"
                v-ripple.400="'rgba(111, 199, 111, 0.15)'"
                pill
                >صعب
              </b-button>
            </div>
          </div>
        </b-col>
        <b-col>
          <label>عدد الأسئلة لهذا النموذج *</label>
          <div
            class="radio-question-num"
            v-for="(question, index) in questions"
            :key="index"
          >
            <b-form-group>
              <b-form-radio
                plain
                class="circle"
                button-variant="danger"
                v-model="selectedQuestion"
                name="radio-questions"
              >
                <span class="radio-label">
                  {{ question }} أسئلة</span
                ></b-form-radio
              >
            </b-form-group>
          </div>
        </b-col>
        <b-col>
          <label for="">صورة الإختبار</label><br>
          <span class="sub mb-2"
            >صورة للإختبارهذه الصورة إختيارية يمكنك تجاوزها</span
          >
          <h1 class="mt-2">
            <div @click="clickItem()" class="custom-add-image">
              <div class="custom-add-text">
                <h4>حمّل صورة تعبر عن أسئلة هذا الإختبار هُنا</h4>
              </div>
            </div>
          </h1>
          <input id="add-picture" type="file" style="visibility: hidden" />
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
  BFormGroup,
  BFormInput,
  BFormDatepicker,
} from "bootstrap-vue";
import Ripple from "vue-ripple-directive";

export default {
  components: {
    BCard,
    BRow,
    BCol,
    BCardText,
    BButton,
    BFormRadio,
    BFormGroup,
    BFormInput,
    BFormDatepicker,
  },
  directives: {
    Ripple,
  },
  data() {
    return {
      questions: [3, 5, 8, 10, 15, 20, 25],
      selectedQuestion: "",
      chosenSpecialty: "",
      specialties: [
        {
          name: "تخصص العلوم العامة للمرحلة الأولى من التعليم الثانوي ",
          image: require("@/assets/images/general.png"),
          value: "general",
        },
        {
          name: "العلمي للمرحلتين الثانية والثالثة من التعليم الثانوي ",
          image: require("@/assets/images/3elmi.png"),
          value: "scientific",
        },
        {
          name: "الأدبي للمرحلتين الثانية والثالثة من التعليم الثانوي",
          image: require("@/assets/images/adabi.png"),
          value: "lit",
        },
      ],
    };
  },
  methods: {
    clickItem() {
      this.$el.querySelector("#add-picture").click();
    },
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
label {
  font-weight: 600;
  font-size: 14px;
  line-height: 27px;

  /* Color/Text */
  color: #303972;
}
.form-control {
  border: 1px solid #c1bbeb;
}
.custom-input-minutes {
  width: 30%;
}
.diff-buttons button {
  margin-right: 5px;
}
.bg-custom-hard {
  background-color: #fb7d5b !important;
  border: none;
}
.bg-custom-medium {
  background-color: #fcc43e !important;
  border: none;
}
.bg-custom-easy {
  background-color: #4D44B5 !important;
  border: none;
}
.radio-label {
  margin-left: 5px;
  font-weight: 400;
  font-size: 14px;
  line-height: 21px;

  /* identical to box height */

  /* Color/Gray 3 */
  color: #a098ae;
}
.custom-add-image {
  border: 5px dashed #c2bbeb81;
  border-style: dashed;
  cursor: pointer;
  text-align: center;
}
.custom-add-text {
  padding: 30%;
}
</style>
