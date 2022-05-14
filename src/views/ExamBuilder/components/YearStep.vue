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
      <b-row>
        <b-col md="4" lg="4">
        
        </b-col>
        <b-col md="4" lg="4"></b-col>
        <b-col md="4" lg="4"></b-col>
      </b-row>
    </b-card>
  </div>
</template>

<script>
import { BCard, BRow, BCol, BCardText, BButton } from "bootstrap-vue";
import Ripple from "vue-ripple-directive";

export default {
  components: {
    BCard,
    BRow,
    BCol,
    BCardText,
    BButton,
  },
  directives: {
    Ripple,
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
</style>