<template>
  <div>
    <!-- card 1 -->
    <b-card header="يرجى إختيار التخصص لهذه لسنة الدراسية">
      <b-card-text>
        في هذه المرحلة من إنشاء إختبار جديد يرجى إختيار التخصص الدراسي بناء على
        السنة الدراسية للطلبة المراد إنشاء إختبار لهم وذلك لأنها الخطوة الأساسية
        قبل البدء في إنشاءه بناء على الاسئلة الموجودة لدينا في قاعدة البيانات،
        الخيارات التالية تشمل السنوات الثلاثة لمرحلة التعليم الثانوي، انقر على
        التخصص المراد إختياره من ثم زر التالي في الأسفل :
      </b-card-text>
      <div class="mt-2">
        <b-media no-body class="mb-2" v-for="(specialty,index) in specialties" :key="index">
          <b-media-aside>
            <b-avatar rounded size="90">
              <b-img
              :src="specialty.image"
              alt="logo"
            />
            </b-avatar>
          </b-media-aside>
          <b-media-body>
            <h5 class="transaction-title">
              {{specialty.name}}
            </h5>
            <b-button
              class="mt-1"
              @click="chooseSpecialty(specialty.value)"
              v-ripple.400="'rgba(40, 199, 111, 0.15)'"
              :variant="chosenSpecialty == specialty.value ? 'success' : 'info'"
              pill
            >
             {{chosenSpecialty == specialty.value ? 'تم الإختيار' : 'إختر التخصص'}} 
            </b-button>
          </b-media-body>
        </b-media>
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
    BMediaBody,
    BMedia,
    BMediaAside,
    BAvatar,
    BImg
  },
  directives: {
    Ripple,
  },
  data() {
    return {
      
      chosenSpecialty: "",
      specialties: [
        { 
          name:'تخصص العلوم العامة للمرحلة الأولى من التعليم الثانوي ',
          image:require('@/assets/images/general.png'),
          value:'general'
        },
        { 
          name:'العلمي للمرحلتين الثانية والثالثة من التعليم الثانوي ',
          image:require('@/assets/images/3elmi.png'),
           value:'scientific'
        },
        { 
          name:'الأدبي للمرحلتين الثانية والثالثة من التعليم الثانوي',
          image:require('@/assets/images/adabi.png'),
          value:'lit'
        },
      ],
    };
  },
  methods:{
    chooseSpecialty(data){
      this.chosenSpecialty = data
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
.transaction-title {
  font-size: 20px;
}
</style>