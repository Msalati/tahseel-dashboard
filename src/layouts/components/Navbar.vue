<template>
  <div class="navbar-container d-flex content align-items-center">

    <!-- Nav Menu Toggler -->
    <ul class="nav navbar-nav d-xl-none">
      <li class="nav-item">
        <b-link
          class="nav-link"
          @click="toggleVerticalMenuActive"
        >
          <feather-icon
            icon="MenuIcon"
            size="21"
          />
        </b-link>
      </li>
    </ul>

    <!-- Left Col -->
    <div class="bookmark-wrapper align-items-center flex-grow-1 d-none d-lg-flex">
      <dark-Toggler class="d-none d-lg-block" />
    </div>
    <div class="search-bar">
      <feather-icon class="custom-search-icon" size="24" icon="SearchIcon" />
      <b-form-input placeholder="هل تبحث عن شيء ما..؟">
      </b-form-input>

    </div>
    <div class="icons-custom">
      <b-button v-ripple.400="'rgba(113, 102, 240, 0.15)'"  variant=" bg-white" class="btn-icon rounded-circle">
        <feather-icon  size="20" icon="BellIcon" />
      </b-button>
      <b-button v-ripple.400="'rgba(113, 102, 240, 0.15)'" variant=" bg-white" class="btn-icon rounded-circle">
        <feather-icon  size="20" icon="SettingsIcon" />
      </b-button>
    </div>
    <b-navbar-nav class="nav align-items-center ml-auto">
      <b-nav-item-dropdown
        right
        toggle-class="d-flex align-items-center dropdown-user-link"
        class="dropdown-user"
      >
        <template #button-content>
          <b-avatar
            size="40"
            variant="light-primary"
            badge
            :src="require('@/assets/images/avatars/1-small.png')"
            class="badge-minimal"
            badge-variant="success"
          />
          <div class="d-sm-flex  d-flex justify-content-start user-nav">
            <p class="user-name font-weight-bolder mb-0">
              لازورد الفيزقة
            </p>
            <span class="user-status custom-user-status">أستاذ</span>
          </div>
        </template>

        <b-dropdown-item link-class="d-flex align-items-center">
          <feather-icon
            size="16"
            icon="UserIcon"
            class="mr-50"
          />
          <span>حسابي</span>
        </b-dropdown-item>

        <b-dropdown-item link-class="d-flex align-items-center">
          <feather-icon
            size="16"
            icon="CheckSquareIcon"
            class="mr-50"
          />
          <span>مهامي</span>
        </b-dropdown-item>

        <b-dropdown-item link-class="d-flex align-items-center">
          <feather-icon
            size="16"
            icon="MessageSquareIcon"
            class="mr-50"
          />
          <span>المحادثات</span>
        </b-dropdown-item>

        <b-dropdown-divider />

        <b-dropdown-item link-class="d-flex align-items-center">
          <feather-icon
            size="16"
            icon="LogOutIcon"
            class="mr-50"
          />
          <span>تسجيل الخروج</span>
        </b-dropdown-item>
      </b-nav-item-dropdown>
    </b-navbar-nav>
  </div>
</template>

<script>
import {
  BLink, BNavbarNav, BNavItemDropdown, BDropdownItem, BDropdownDivider, BAvatar, BButton, BFormInput
} from 'bootstrap-vue'
import DarkToggler from '@core/layouts/components/app-navbar/components/DarkToggler.vue'

export default {
  components: {
    BLink,
    BNavbarNav,
    BNavItemDropdown,
    BDropdownItem,
    BDropdownDivider,
    BAvatar,
    BButton,
    BFormInput,
    // Navbar Components
    DarkToggler,
  },
  props: {
    toggleVerticalMenuActive: {
      type: Function,
      default: () => {},
    },
  },
}
</script>
<style scoped>
.custom-user-status{
  text-align: right !important;
  color: red !important;
}
.icons-custom{
  margin-top: 14px;
  margin-right: 30px;
}
.icons-custom>:first-child{
  margin-right: 10px;
}

.search-bar{
  margin-right: 30px;
  margin-top: 14px;
}
.search-bar input{
  border-radius: 30px;
  box-shadow: none;
  border: none;
  padding: 10px;
}
.search-bar{
  display: flex;
}
.custom-search-icon{
  position: absolute;
  right: 350px;
   text-indent: -999px;
  overflow: hidden;
  width: 40px;
  padding: 0;
  margin: 0;
  margin-top: 7px;
  border: 1px solid transparent;
  border-radius: inherit;
  cursor: pointer;
  opacity: 0.7;
  color: #4D44B5;
    transform: scaleX(-1);
}
</style>
