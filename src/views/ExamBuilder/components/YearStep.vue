<template>
  <div>
    <!-- card 1 -->
    <b-card header="يرجى إختيار السنة الدراسية">
      <b-card-text>
        في هذه المرحلة من إنشاء إختبار جديد يرجى إختيار السنة الدراسية للطلبة
        المراد إنشاء إختبار لها وذلك لأنها الخطوة الأساسية قبل البدء في إنشاءه
        بناء على الاسئلة الموجودة لدينا في قاعدة البيانات، الخيارات التالية
        تتمثل في السنوات الثلاثة لمرحلة التعليم الثانوي بغض النظر عن التخصص
        العلمي والأدبي، انقر على السنة من ثم زر التالي في الأسفل :
      </b-card-text>
      <b-row class="mt-5">
        <b-col md="4" lg="4">
          <b-card
            :img-src="require('@/assets/images/Group 13983.png')"
            overlay
            text-variant="white"
            img-alt="card img"
            body-class="bg-overlay"
          >
          </b-card>
          <div class="radio">
          <b-form-radio
            v-model="year"
            name="some-radio9"
            value="e"
            class="custom-control-primary"
          >
            المرحلة الأولى من التعليم الثانوي
          </b-form-radio>
          </div>
        </b-col>
        <b-col md="4" lg="4">
          <b-card
            :img-src="require('@/assets/images/Group 13984.png')"
            overlay
            text-variant="white"
            img-alt="card img"
            body-class="bg-overlay"
          >
          </b-card>
         <div class="radio">
            <b-form-radio
              v-model="year"
              name="some-radio9"
              value="ff"
              class="custom-control-primary"
            >
               المرحلة الثانية من التعليم الثانوي
            </b-form-radio>
         </div>
        </b-col>
        <b-col md="4" lg="4">
          <b-card
            :img-src="require('@/assets/images/placeholder.png')"
            overlay
            text-variant="white"
            img-alt="card img"
            body-class="bg-overlay"
          >
          </b-card>
        <div class="radio">
            <b-form-radio
              v-model="year"
              name="some-radio9"
              value="g"
              class="custom-control-primary"
            >
               المرحلة الثالثة من التعليم الثانوي
            </b-form-radio>
        </div>
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
  },
  directives: {
    Ripple,
  },
  data(){
    return {
      year:""
    }
  }
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
 .custom-radio .custom-control-label::before{
   border-radius: 3px;
   border: #a098ae solid 2px;
 }
 .radio{
   padding: 10px;
   background: #FCFCFC;
   border-radius: 14px;
 }
 .custom-checkbox .custom-control-label, .custom-radio .custom-control-label{
   font-size: 16px;
 }
</style>