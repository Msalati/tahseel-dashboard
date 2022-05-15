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
              <div>مدة الإمتحان: 2 ساعة</div>
              <div>عدد الأسئلة: 15 سؤال</div>
              <div>المادة: رياضيات</div>
            </div>
          </div>
          <div class="block">
            <div class="logo-wrapper">
              <logo />
              <h3 class="text-primary invoice-logo"></h3>
            </div>
            <h3>مدرسة {school-name-here}</h3>
            <h3>اسئلة امتحان {exam-type-here}</h3>
            <h3>2021-2022</h3>
          </div>
          <div class="block mt-4">
            <div class="exam-header-left-side">
              <div>
                إسم الطالب: ..............................................
              </div>
              <div>
                رقم الطالب: ..............................................
              </div>
              <div>تاريخ الإمتحان {date-here}</div>
            </div>
          </div>
        </div>
        <div class="divider"></div>
        <div class="questions">
          <div class="question">
            <h4>س{index} - {question} ?</h4>
          </div>
        </div>
      </div>
    </b-card>
  </section>
</template>

<script>
import {
  BRow,
  BCol,
  BCard,
  BCardBody,
  BTableLite,
  BCardText,
  BButton,
  BAlert,
  BLink,
  VBToggle,
} from "bootstrap-vue";
import Logo from "@core/layouts/components/Logo.vue";
import Ripple from "vue-ripple-directive";

export default {
  data() {
    return {
      exam: {
        title: "الفصل الدراسي الأول",
        teacher: "لازورد الفيزقة",
        year: "2022",
        time: "120",
        subject: "الرياضيات",

        questions: [
          {
            image: "www.lorepicsum.com/200",
            question: "ماهو حاصل جمع 1+1؟",
            answer: "2",
            type: "direct",
          },
          {
            image: "www.lorepicsum.com/200",
            question: "ماهو حاصل جمع 1+1؟",
            answer: "2",
            type: "direct",
          },
          {
            image: "www.lorepicsum.com/200",
            question: "ماهو حاصل جمع 1+1؟",
            answer: "2",
            type: "direct",
          },
          {
            image: "www.lorepicsum.com/200",
            question: "ماهو حاصل جمع 1+1؟",
            answer: "2",
            type: "direct",
          },
          {
            image: "www.lorepicsum.com/200",
            question: "ماهو حاصل جمع 1+1؟",
            answer: "2",
            type: "direct",
          },
          {
            image: "www.lorepicsum.com/200",
            question: "ماهو حاصل جمع 1+1؟",
            answer: "2",
            type: "direct",
          },
          {
            image: "www.lorepicsum.com/200",
            question: "ماهو حاصل جمع 1+1؟",
            answer: "2",
            type: "direct",
          },
          {
            image: "www.lorepicsum.com/200",
            question: "ماهو حاصل جمع 1+1؟",
            answer: "2",
            type: "direct",
          },
          {
            image: "www.lorepicsum.com/200",
            question: "ماهو حاصل جمع 1+1؟",
            answer: "2",
            type: "direct",
          },
        ],
      },
    };
  },
  directives: {
    Ripple,
    "b-toggle": VBToggle,
  },
  components: {
    BRow,
    BCol,
    BCard,
    BCardBody,
    BTableLite,
    BCardText,
    BButton,
    BAlert,
    BLink,

    Logo,
  },
  methods: {
    printInvoice() {
      var el = this.$el.querySelector(".hideTempo");
      el.style.display = "none";
      window.print();
      el.style.display = "block";
    },
  },
  setup() {
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
      printInvoice,
    };
  },
};
</script>

<style lang="scss" scoped>
@import "~@core/scss/base/pages/app-invoice.scss";
</style>

<style lang="scss">
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
      font-size: 20px !important;
      font-weight: 800;
    }
    .bg-custom-print {
      font-size: 36px;
    }
  }
}
</style>
