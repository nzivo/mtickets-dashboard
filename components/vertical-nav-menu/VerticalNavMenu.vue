<template>
  <v-navigation-drawer
    :value="isDrawerOpen"
    app
    floating
    width="260"
    class="app-navigation-menu"
    :right="$vuetify.rtl"
    @input="(val) => $emit('update:is-drawer-open', val)"
  >
    <!-- Navigation Header -->
    <div class="vertical-nav-header d-flex items-center ps-6 pe-5 pt-5 pb-2">
      <NuxtLink to="/" exact class="d-flex align-center text-decoration-none">
        <v-img
          :src="require('@/assets/images/logos/mticket-logo.png')"
          max-height="42px"
          max-width="125px"
          alt="M-Tickets"
          contain
          eager
          class="app-logo me-3"
        ></v-img>
      </NuxtLink>
    </div>

    <!-- Navigation Items -->
    <v-list expand shaped class="vertical-nav-menu-items pr-5">
      <nav-menu-link
        title="Dashboard"
        to="/"
        :icon="icons.mdiHomeOutline"
      ></nav-menu-link>
      <nav-menu-link
        title="Account Settings"
        to="/account-settings"
        :icon="icons.mdiAccountCogOutline"
      ></nav-menu-link>
      <nav-menu-group title="Pages" :icon="icons.mdiFileOutline">
        <nav-menu-link
          title="Login"
          to="/login"
          target="_blank"
        ></nav-menu-link>
        <nav-menu-link
          title="Register"
          to="/register"
          target="_blank"
        ></nav-menu-link>
        <nav-menu-link
          title="Error"
          to="/error"
          target="_blank"
        ></nav-menu-link>
      </nav-menu-group>
      <nav-menu-section-title title="USER INTERFACE"></nav-menu-section-title>
      <nav-menu-link
        title="Typography"
        to="/typography"
        :icon="icons.mdiAlphaTBoxOutline"
      ></nav-menu-link>
      <nav-menu-link
        title="Icons"
        to="/icons"
        :icon="icons.mdiEyeOutline"
      ></nav-menu-link>
      <nav-menu-link
        title="Cards"
        to="/card"
        :icon="icons.mdiCreditCardOutline"
      ></nav-menu-link>
      <nav-menu-link
        title="Tables"
        to="/simple-table"
        :icon="icons.mdiTable"
      ></nav-menu-link>
      <nav-menu-link
        title="Form Layouts"
        to="/form-layouts"
        :icon="icons.mdiFormSelect"
      ></nav-menu-link>
    </v-list>
    <a
      href="https://themeselection.com/products/materio-vuetify-vuejs-admin-template"
      target="_blank"
      rel="nofollow"
    >
      <v-img
        :src="
          require(`@/assets/images/pro/upgrade-banner-${
            $vuetify.theme.dark ? 'dark' : 'light'
          }.png`)
        "
        alt="upgrade-banner"
        transition="scale-transition"
        class="upgrade-banner mx-auto"
        max-width="230"
      ></v-img>
    </a>
  </v-navigation-drawer>
</template>

<script>
// eslint-disable-next-line object-curly-newline
import {
  mdiHomeOutline,
  mdiAlphaTBoxOutline,
  mdiEyeOutline,
  mdiCreditCardOutline,
  mdiTable,
  mdiFileOutline,
  mdiFormSelect,
  mdiAccountCogOutline,
} from '@mdi/js'
import NavMenuSectionTitle from './components/NavMenuSectionTitle.vue'
import NavMenuGroup from './components/NavMenuGroup.vue'
import NavMenuLink from './components/NavMenuLink.vue'

export default {
  components: {
    NavMenuSectionTitle,
    NavMenuGroup,
    NavMenuLink,
  },
  props: {
    isDrawerOpen: {
      type: Boolean,
      default: null,
    },
  },
  setup() {
    return {
      icons: {
        mdiHomeOutline,
        mdiAlphaTBoxOutline,
        mdiEyeOutline,
        mdiCreditCardOutline,
        mdiTable,
        mdiFileOutline,
        mdiFormSelect,
        mdiAccountCogOutline,
      },
    }
  },
}
</script>

<style lang="scss" scoped>
@import '~/plugins/vuetify/default-preset/preset/overrides.scss';

.app-title {
  font-size: 1.25rem;
  font-weight: 700;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: 0.3px;
}

// ? Adjust this `translateX` value to keep logo in center when vertical nav menu is collapsed (Value depends on your logo)
.app-logo {
  transition: all 0.18s ease-in-out;
  .v-navigation-drawer--mini-variant & {
    transform: translateX(-4px);
  }
}

@include theme(app-navigation-menu) using ($material) {
  background-color: map-deep-get($material, 'background');
}

.app-navigation-menu {
  .v-list-item {
    &.vertical-nav-menu-link {
      ::v-deep .v-list-item__icon {
        .v-icon {
          transition: none !important;
        }
      }
    }
  }
}

// You can remove below style
// Upgrade Banner
.app-navigation-menu {
  .upgrade-banner {
    position: absolute;
    bottom: 13px;
    left: 50%;
    transform: translateX(-50%);
  }
}
</style>
