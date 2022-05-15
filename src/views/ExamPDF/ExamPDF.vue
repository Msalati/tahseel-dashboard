<template>
  <section class="invoice-preview-wrapper">
    <!-- Alert: No item found -->

    <div class="text-right mb-2 hideTempo">
      <b-row>
        <b-col class="text-left mt-2">
          <h2>نموذج الأسئلة</h2>
        </b-col>
        <b-col>
          <b-button
            class="mt-1 color-primary bg-custom-print text-left p-2"
            v-ripple.400="'rgba(40, 199, 111, 0.15)'"
            pill
            variant="primary"
            @click="printInvoice"
          >
            <feather-icon class="mr-1" icon="PrinterIcon" size="16" />طباعة
          </b-button>
        </b-col>
      </b-row>
    </div>
    <b-card>
      <div class="exam-paper">
        <div class="exam-header d-flex justify-content-around text-center">
          <div class="block mt-4 text-right">
            <div class="exam-header-right-side">
              <div>مدة الإمتحان: {{ exam.time / 60 }} ساعة</div>
              <div>عدد الأسئلة: {{ exam.questions.length }} سؤال</div>
              <div>المادة: {{ exam.subject }}</div>
            </div>
          </div>
          <div class="block">
            <div class="logo-wrapper">
              <logo />
              <h3 class="text-primary invoice-logo"></h3>
            </div>
            <h3>مدرسة {{ exam.school }}</h3>
            <h3>اسئلة امتحان {{ exam.title }}</h3>
            <h3>{{ exam.year }}</h3>
          </div>
          <div class="block mt-4">
            <div class="exam-header-left-side">
              <div>
                إسم الطالب: ..............................................
              </div>
              <div>
                رقم الطالب: ..............................................
              </div>
              <div>تاريخ الإمتحان {{ getDate() }}</div>
            </div>
          </div>
        </div>
        <div class="divider"></div>
        <div class="questions">
          <div
            class="question"
            v-for="(question, index) in exam.questions"
            :key="index"
          >
            <h4 class="question-item">س{{ index + 1 }} - {{ question.question }}</h4>
            <h4 class="answers" v-for="(choice, index) in question.choises" :key="index">
              {{ index + 1 }}- {{ choice }}
            </h4>
          </div>
        </div>
      </div>
    </b-card>


    <!-- answers -->
    
    <div class="text-right mb-2 hideTempo">
      <b-row>
        <b-col class="text-left mt-2">
          <h2>نموذج الأجوبة</h2>
        </b-col>
        <b-col>
          <b-button
            class="mt-1 color-primary bg-custom-print text-left p-2"
            v-ripple.400="'rgba(40, 199, 111, 0.15)'"
            pill
            variant="primary"
            @click="printInvoice"
          >
            <feather-icon class="mr-1" icon="PrinterIcon" size="16" />طباعة
          </b-button>
        </b-col>
      </b-row>
    </div>
    <b-card>
      <div class="exam-paper">
        <div class="exam-header d-flex justify-content-around text-center">
          <div class="block mt-4 text-right">
            <div class="exam-header-right-side">
              <div>مدة الإمتحان: {{ exam.time / 60 }} ساعة</div>
              <div>عدد الأسئلة: {{ exam.questions.length }} سؤال</div>
              <div>المادة: {{ exam.subject }}</div>
            </div>
          </div>
          <div class="block">
            <div class="logo-wrapper">
              <logo />
              <h3 class="text-primary invoice-logo"></h3>
            </div>
            <h3>مدرسة {{ exam.school }}</h3>
            <h3>اسئلة امتحان {{ exam.title }}</h3>
            <h3>{{ exam.year }}</h3>
            <h3 class="success">نموذج الإجابة</h3>
          </div>
          <div class="block mt-4">
            <div class="exam-header-left-side">
              <div>
                إسم الطالب: ..............................................
              </div>
              <div>
                رقم الطالب: ..............................................
              </div>
              <div>تاريخ الإمتحان {{ getDate() }}</div>
            </div>
          </div>
        </div>
        <div class="divider"></div>
        <div class="questions">
          <div
            class="question"
            v-for="(question, index) in exam.questions"
            :key="index"
          >
            <h4 class="question-item">س{{ index + 1 }} - {{ question.question }}</h4>
            <h4 class="answers">
               {{ question.correctAnswer }}
            </h4>
          </div>
        </div>
      </div>
    </b-card>
  </section>
</template>

<script>
import { BRow, BCol, BCard, BButton, VBToggle } from "bootstrap-vue";
import Logo from "@core/layouts/components/Logo.vue";
import Ripple from "vue-ripple-directive";
import { ref } from "@vue/composition-api";

export default {
  data() {
    return {};
  },
  directives: {
    Ripple,
    "b-toggle": VBToggle,
  },
  components: {
    BRow,
    BCol,
    BCard,
    BButton,

    Logo,
  },
  methods: {
    printInvoice() {
      var el = this.$el.querySelector(".hideTempo");
      el.style.display = "none";
      window.print();
      el.style.display = "block";
    },
    getDate() {
      var date = new Date();
      return date.toLocaleDateString();
    },
  },
  setup() {
    let exam = ref({
      title: "الفصل الدراسي الأول",
      teacher: "لازورد الفيزقة",
      year: "2021-2022",
      school: "دار اليمامة التعليمية",
      time: "120",
      subject: "تقنية معلومات",
      date: Date.now(),
      questions: [
        {
          id: 1,
          question: "ما هو الشيء الوحيد الذي تفهمه أجهزة الكمبيوتر؟",
          correctAnswer: "Machine Code",
          choises: ["Machine Code", "Algorithms", "High Level Languages"],
        },
        {
          id: 2,
          question: "يُعرف حل الأخطاء في البرنامج بـ ...",
          correctAnswer: "Problem Solving",
          choises: ["Debugging", "Error Checking", "Problem Solving"],
        },
        {
          id: 3,
          question: "ماذا يعني الرمز الثنائي؟",
          correctAnswer: "a coding system using the binary digits 0 and 1. ",
          choises: [
            "a coding system using the binary digits 0 and 1",
            "1000100100",
            "a coding system using the binary digits 1-10 ",
          ],
        },
        {
          id: 4,
          question:
            "ما نوع الذاكرة المستخدمة عند الحاجة الى تخزين بيانات بشكل دائم؟",
          correctAnswer: "ROM",
          choises: ["ROM", "RAM", "CPU"],
        },
        {
          id: 5,
          question: "أي البيانات التالية مهمة في استخدام الحاسوب الشخصي؟",
          correctAnswer: "نظام التشغيل",
          choises: ["قاعدة البيانات", "نظام التشغيل", "جدول بيانات"],
        },
        {
          id: 6,
          question: "بماذا تتمثل أهمية Google Drive?",
          correctAnswer: "جميع ما ذكر",
          choises: ["مشاركة الملفات", "تخزين الملفات", "جميع ما ذكر"],
        },
        {
          id: 7,
          question: "تستخدم كلمة المرور في؟",
          correctAnswer: "حماية الحاسوب من المستخدمين",
          choises: [
            "تسهيل وصول الىمعلومات الحاسوب",
            "تسهيل الوصول الى الشبكة",
            "حماية الحاسوب من المستخدمين",
          ],
        },
        {
          id: 8,
          question: "ما هو البرنامج المسؤول عن ادراج وعرض شرائح تقديمية؟",
          correctAnswer: "POWERPOINT",
          choises: ["PUPBLISHER", "POWERPOINT", "EXCEL"],
        },
        {
          id: 9,
          question: "أكثر أنواع الملفات الصوتية استخداما بالأنترنت؟",
          correctAnswer: "MP3",
          choises: ["WAV", "MP4", "MP3"],
        },
        {
          id: 10,
          question: "تتكون الصور من نقاط صغيرة تسمى؟",
          correctAnswer: "بكسل",
          choises: ["بايت", "نقطة", "بكسل"],
        },
      ],
    });
    const invoiceDescription = [
      {
        taskTitle: "Native App Development",
        taskDescription:
          "Developed a full stack native app using React Native, Bootstrap & Python",
        rate: "$60.00",
        hours: "30",
        total: "$1,800.00",
      },
      {
        taskTitle: "UI Kit Design",
        taskDescription:
          "Designed a UI kit for native app using Sketch, Figma & Adobe XD",
        rate: "$60.00",
        hours: "20",
        total: "$1200.00",
      },
    ];

    return {
      invoiceDescription,
      exam,
    };
  },
  mounted() {},
};
</script>

<style lang="scss" scoped>
@import "~@core/scss/base/pages/app-invoice.scss";
</style>

<style lang="scss">
.question {
  margin-top: 30px;
  font-weight: bold;
  font-size: 26px;
}
.question .question-item{
  font-weight: 600;
}
.answers{
  margin-top: 20px;
}
@media print {
  // Global Styles
  body {
    background-color: transparent !important;
  }
  nav.header-navbar {
    display: none;
  }
  .main-menu {
    display: none;
  }
  .header-navbar-shadow {
    display: none !important;
  }
  .content.app-content {
    margin-left: 0;
    padding-top: 2rem !important;
  }
  footer.footer {
    display: none;
  }
  .card {
    background-color: transparent;
    box-shadow: none;
  }
  .customizer-toggle {
    display: none !important;
  }
  // Invoice Specific Styles
  .invoice-preview-wrapper {
    .row.invoice-preview {
      .col-md-8 {
        max-width: 100%;
        flex-grow: 1;
      }

      .invoice-preview-card {
        .card-body:nth-of-type(2) {
          .row {
            > .col-12 {
              max-width: 50% !important;
            }

            .col-12:nth-child(2) {
              display: flex;
              align-items: flex-start;
              justify-content: flex-end;
              margin-top: 0 !important;
            }
          }
        }
      }
    }

    .exam-header {
      text-align: center;
      display: flex !important;
      flex-direction: row;
      justify-content: space-evenly;
    }
    .block * {
      font-weight: bolder !important;
    }
    .exam-header-right-side {
      text-align: right;
    }
    .exam-header-left-side {
      text-align: right;
    }
    .exam-header-left-side,
    .exam-header-right-side {
      margin-top: 70px;
    }
    // Action Right Col
    .invoice-actions {
      display: none;
    }
    .divider {
      height: 2px;
      width: 100%;
      padding: 0px;
      border: 2px solid black;
    }
    .question h4 {
    }
    .bg-custom-print {
      font-size: 36px;
    }
  }
}
</style>
