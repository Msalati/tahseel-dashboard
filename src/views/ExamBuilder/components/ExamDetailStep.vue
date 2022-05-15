<template>
  <div>
    <!-- card 1 -->
    <b-card header="يرجى تحديد التفاصيل التالية للإختبار">
      <div class="mt-2 questions">
        <b-row>
          <b-col>
            <div class="mt-2">
              <h5>إسم نموذج الإختبار *</h5>
              <b-form-input placeholder="إختبار نهاية الفصل الأول"
                >hello</b-form-input
              >
            </div>

            <div class="mt-4">
              <h5>تاريخ بدء وإنتهاء الإختبار *</h5>
              <b-row class="mt-2">
                <b-col>
                  <b-form-input
                    aria-placeholder="2022/3/4"
                    type="date"
                    placeholder="إختبار نهاية الفصل الأول"
                    >hello</b-form-input
                  ></b-col
                >
                <b-col>
                  <b-form-input
                    aria-placeholder="2022/3/4"
                    type="date"
                    placeholder="إختبار نهاية الفصل الأول"
                    >hello</b-form-input
                  >
                </b-col>
              </b-row>
            </div>

            <div class="mt-5 custom-question">
              <b-row>
                <b-col md="6"
                  ><h5>كم أقصى موعد يمكن أن يستغرقه الطالب للحل؟ *</h5>
                </b-col>
                <b-col md="6" class="d-flex justify-content-around custom-time">
                  <feather-icon
                    class="text-warning"
                    icon="ClockIcon"
                    size="25"
                  />
                  <span>الزمن بالدقائق </span>
                  <b-form-input
                    placeholder="20"
                    class="custom-input-minutes "
                  ></b-form-input>
                </b-col>
              </b-row>
            </div>

            <div class="mt-4">
              <h5>مستوى تعقيد الإختبار*</h5>
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
            <b-row>
              <b-col>
                <div class="mt-2">
                  <h5 class="mb-2">عدد الأسئلة لهذا النموذج *</h5>
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
                </div>
              </b-col>
              <b-col class="mt-2">
                <h5>صورة الإختبار</h5>
                <span class="sub"
                  >صورة للإختبارهذه الصورة إختيارية يمكنك تجاوزها</span
                >
                <h1>
                  <div @click="clickItem()" class="custom-add-image mt-2">
                    <div class="custom-add-text">
                      <h4>حمّل صورة تعبر عن أسئلة هذا الإختبار هُنا</h4>
                    </div>
                  </div>
                </h1>
                <input
                  id="add-picture"
                  type="file"
                  style="visibility: hidden"
                />
              </b-col>
            </b-row>
          </b-col>
        </b-row>
      </div>
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
  BMediaBody,
  BMedia,
  BMediaAside,
  BImg,
  BAvatar,
  BFormInput,
  BFormFile,
  BFormRadioGroup,
  BFormGroup,
} from "bootstrap-vue";
import Ripple from "vue-ripple-directive";
import FileUpload from "v-file-upload";

export default {
  components: {
    BCard,
    BRow,
    BCol,
    BFormGroup,
    BFormRadio,
    FileUpload,
    BCardText,
    BButton,
    BMediaBody,
    BFormFile,
    BFormRadioGroup,
    BMedia,
    BMediaAside,
    BAvatar,
    BImg,
    BFormInput,
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
    chooseSpecialty(data) {
      this.chosenSpecialty = data;
    },
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
.transaction-title {
  font-size: 20px;
}
.questions h5 {
  color: #303972;
  font-weight: bold;
}
.custom-question {
}
.custom-question span {
  font-size: 12px;
  padding: 4px;
}
.custom-time {
}
.diff-buttons button {
  margin-right: 16px;
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
.radio-question-num .custom-radio {
  margin: 30px;
  margin-top: 10px;
  margin-bottom: 14px;
  font-size: 10px;
}
.radio-question-num .custom-radio span {
  color: #a098ae !important;
}
.radio-question-num-other {
  display: inline-flex;
}
.radio-test {
  border-radius: 300px;
}
.custom-upload {
  height: 30px;
  width: 100%;
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
