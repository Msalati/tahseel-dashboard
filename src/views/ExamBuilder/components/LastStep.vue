<template>
  <div>
    <!-- card 1 -->
    <b-card header="الإختبار جاهز للنشر 🥳">
      <b-card-text>
        في هذه المرحلة من إنشاء إختبار جديد يرجى إختيار المقرر الدراسي المراد
        إنشاء اختبار له وذلك بعد الحرص على إختيار الفصل الدراسي قبل، يمكنك
        اختيار الفصلين معا من خلالا اختيار نهاية السنة الدراسية أو اختيار كل فصل
        على حدا، عندما تنتهي من اخيار الفصل والمقرر المراد إختياره انقر زر
        التالي في الأسفل :
      </b-card-text>
      <b-row>
        <b-col>
          <div class="pole"></div>
          <b-card img-alt="Card image cap" class="card-test" img-top no-body>
            <b-card-body>
              <b-card-title class="title"
                >إختبار نهاية الفصل الأول</b-card-title
              >
              <b-card-subtitle class="subtitle"
                >إعداد : لازورد الفيزقة</b-card-subtitle
              >
              <b-badge variant="primary" class="float-right"> سهل </b-badge>
              <b-card-text class="mt-4">
                <span>
                  <feather-icon
                    class="text-warning"
                    icon="ClockIcon"
                    size="15"
                  />
                  موعد البداية : 2022/11/16 موعد الإنتهاء : 2022/11/18 </span
                ><br />
                <span>
                  <feather-icon
                    class="text-info"
                    icon="CalendarIcon"
                    size="15"
                  />
                  زمن الإمتحان: 20 دقيقة
                </span>
              </b-card-text>
            </b-card-body>
            <b-card-footer class="row justify-content-between">
              <div class="col-6"><h5 class="year">اولى ثانوي</h5></div>

              <div class="col-6 text-center">
                <h5>عدد الأسئلة</h5>
                <span class="questions">10</span>
              </div>
            </b-card-footer>
          </b-card>
        </b-col>
        <b-col>
        <b-img src="@/assets/images/books.png"></b-img>
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
  BCardBody,
  BImg,
  BCardTitle,
  BCardSubTitle,
  BCardFooter,
} from "bootstrap-vue";
import Ripple from "vue-ripple-directive";

export default {
  components: {
    BCard,
    BRow,
    BCardBody,
    BFormCheckbox,
    BCol,
    BImg,
    BCardText,
    BButton,
    BFormRadio,
    BBadge,
    BCardTitle,
    BCardFooter,
    BCardSubTitle,
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
.card-test {
  filter: drop-shadow(0px 4px 10px rgba(77, 68, 181, 0.1));
  padding: 30px;
  border-radius: 20px;
}
.pole {
  position: absolute;
  width: 24px;
  height: 92%;
  left: 0;
  z-index: 1;
  /* Color/Orange */
  background: #fb7d5b;
  border-radius: 0px 20px 20px 0px;
  transform: matrix(-1, 0, 0, 1, 0, 0);
}
.title {
  font-weight: 600;
  font-size: 20px;
  line-height: 30px;
  margin-bottom: 0 !important;
  /* identical to box height */

  /* Color/Text */
  color: #303972;
}
.subtitle {
  font-weight: 400;
  font-size: 16px;
  line-height: 24px;

  /* identical to box height */

  /* Color/Gray 3 */
  color: #a098ae;
}
.card-text {
  font-size: 13px;
}
.questions {
  font-weight: 600;
  font-size: 36px;
  line-height: 54px;

  /* identical to box height */

  /* Color/Text */
  color: #303972;
}
.year {
  font-weight: 400;
  font-size: 25.0504px;
  line-height: 48px;
  letter-spacing: 0.22267px;
}
</style>