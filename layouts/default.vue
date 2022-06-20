<template lang="pug">
  v-app(light)
    v-app-bar(outlined elevation="0" :height="84" color="#3044B8" app)
      v-container.py-2.d-flex(style="align-items: center")
          div.d-flex(style="flex-direction: column; color: white; align-items: center; text-align: center; width: 200px")
                div(style="font-weight: bold; font-size: 20px; width: 86px") JOB
                div(style="font-weight: bold; font-size: 20px; width: 86px") ONLINE
                div(style="font-size: 11px; width: 78px; text-align: center") Uy tín là số 1  
          v-spacer       
          div.mx-2(style="text-align: center; color: white")
            img.hide-xs-only(:src="require('/assets/images/zalo1.svg')" :height="24")
            .text-xs {{listNumber[random - 1]}}
          div.mx-2(style="text-align: center; color: white")
            img.hide-xs-only(:src="require('/assets/images/mail1.svg')" :height="24")
            .text-xs hr.vieclamonline@gmail.com
    v-main
      v-carousel.carousel(  height="600" hide-delimiter-background show-arrows-on-hover)
            v-carousel-item.carousel-item(v-for="(slide, i) in slides" :key="i" :src="slide.img" style="position: relative")
                div.d-flex(style="position: absolute; left: 30px; bottom: 30px; flex-direction: column")
                    img.text-title(:src="slide.title")
                    v-btn.btn-text(:width="120" style="color: #3044B8" @click="overlay = true") 
                        v-icon(left) mdi-comment-text
                        span Nhắn Tin
      v-container.my-5(style="position: relative")
        img.float(:src="require('/assets/images/zalo2.svg')" :width="28" :height="28" @click="overlay = true")
        .d-flex.mt-4.py-4.list-icon(style="justify-content: space-around")
            img.my-2(:src="require('/assets/images/round1.svg')" height="300")
            img.my-2(:src="require('/assets/images/round2.svg')" height="300")
            img.my-2(:src="require('/assets/images/round3.svg')" height="300")
        .d-flex.mt-4.py-4.list-icon(style="justify-content: space-between")
            div(style="width: 100%; text-align: justify; height: 485px; max-width: 598px")
                h1(style="text-align: center; color: #3044B8") Mô tả công việc
                ul(style="width: 100%; text-align: justify; height: 500px; line-height: 40px; font-size: 22px;")
                    li.my-1 Nhận hướng dẫn và tài liệu cần xử lý từ Quản lý qua điện thoại và Zalo cá nhân
                    li.my-1 Hoàn thành các thao tác nhập liệu theo người hướng dẫn
                    li.my-1 Sau khi hoàn thành, gửi lại báo cáo cho Quản lý trực tiếp
                    li.my-1 Sau khi Quản lý kiểm tra đúng và đầy đủ thông tin, tiền công sẽ được chuyển vào số tài khoản ngân hàng đã cung cấp
                    li.my-1 Thu nhập 1 ngày từ 
                       span(style="font-weight: bold") 300.000 đến 1.500.000 đồng.
            img.ml-3(:src="require('/assets/images/illus.png')" style="width: 100%; max-width: 598px; height: 485px; object-fit: contain")
    div.image-bg.mt-5.py-4.mx-auto
        h1(style="color: white; text-align: center") YÊU CẦU
        .d-flex.mt-3.list-icon(style="justify-content: center")
            img.my-2(:src="require('/assets/images/card1.svg')" height="300")
            img.my-2(:src="require('/assets/images/card2.svg')" height="300")
            img.my-2(:src="require('/assets/images/card3.svg')" height="300")
            img.my-2(:src="require('/assets/images/card4.svg')" height="300")
    v-overlay( :absolute="absolute"
          :opacity="opacity"
          :value="overlay")
        .d-flex(style="flex-direction: column")  
            h1.my-3(style="text-align: center") Quét Mã Zalo:
            img.my-3.carousel-item.pa-2(v-if="random != 0" :src="require(`/assets/images/popup-${random}.png`)")
            v-btn.my-3.carousel-item.pa-2(color="#3044B8" @click="overlay = false") Đóng
</template>

<script>
  export default {
    name: "DefaultLayout",
    data() {
      return {
        listNumber: [
          "+84 582 341 948",
          "+84 587 832 546",
          "+84 817 790 471",
          "+84 339 990 129",
          "+84 343 270 850",
          "+84 582 962 877"
        ],
        overlay: false,
        absolute: false,
        opacity: 0.9,
        random: 0,
        slides: [
          {
            title: require("/assets/images/text1.svg"),
            img: require("/assets/images/banner1.png")
          },
          {
            title: require("/assets/images/text2.svg"),
            img: require("/assets/images/banner2.png")
          },
          {
            title: require("/assets/images/text3.svg"),
            img: require("/assets/images/banner3.png")
          }
        ]
      }
    },
    mounted() {
      this.random = Math.floor(Math.random() * (6 - 1 + 1) + 1)
    }
  }
</script>
<style>
  htm,
  body {
    font-family: Arial, Helvetica, sans-serif;
  }
  .image-bg {
    background: url("./assets/images/unsplash.png");
    width: 100%;
  }
  .float {
    position: fixed;
    width: 60px;
    height: 60px;
    bottom: 40px;
    right: 40px;
    border-radius: 50px;
    background: white;
    text-align: center;
    box-shadow: 2px 2px 3px black;
    cursor: pointer;
  }

  @media screen and (max-width: 991px) {
    .carousel-item {
      width: 100%;
    }
    .list-icon {
      flex-direction: column;
      align-items: center;
    }
  }
  @media screen and (max-width: 767px) {
    .text-title {
      width: 90%;
      margin-bottom: 1rem;
    }
    .btn-text {
      margin-bottom: 1rem;
    }
    .carousel,
    .v-window__container,
    .v-carousel__item {
      height: 300px !important;
    }
    .hide-xs-only {
      display: none;
    }
    .text-xs {
      word-break: break-word;
    }
  }
</style>
