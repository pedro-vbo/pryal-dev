<template>
  <!--begin::Menu-->
  <div
    class="menu menu-sub menu-sub-dropdown menu-column menu-rounded menu-gray-600 menu-state-bg-light-primary fw-bold py-4 fs-6 w-275px"
    data-kt-menu="true"
  >
    <!--begin::Menu item-->
    <div class="menu-item px-3">
      <div class="menu-content d-flex align-items-center px-3">
        <!--begin::Avatar-->
        <div class="symbol symbol-50px me-5">
          <img alt="Logo" src="media/avatars/150-2.jpg" />
        </div>
        <!--end::Avatar-->

        <!--begin::Username-->
        <div class="d-flex flex-column">
          <div class="fw-bolder d-flex align-items-center fs-5">
            Max Smith
            <span
              class="badge badge-light-success fw-bolder fs-8 px-2 py-1 ms-2"
              >Pro</span
            >
          </div>
          <a href="#" class="fw-bold text-muted text-hover-primary fs-7"
            >max@kt.com</a
          >
        </div>
        <!--end::Username-->
      </div>
    </div>
    <!--end::Menu item-->

    <!--begin::Menu separator-->
    <div class="separator my-2"></div>
    <!--end::Menu separator-->

    <!--begin::Menu item-->
    <div class="menu-item px-5">
      <router-link to="/pages/profile/overview" class="menu-link px-5">
        My Profile
      </router-link>
    </div>
    <!--end::Menu item-->
    <!--begin::Menu item-->
    <div class="menu-item px-5">
      <a @click="signOut()" class="menu-link px-5">
        Sign Out
      </a>
    </div>
    <!--end::Menu item-->
  </div>
  <!--end::Menu-->
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { useStore } from "vuex";
import { useRouter } from "vue-router";
import { Actions } from "@/store/enums/StoreEnums.ts";

export default defineComponent({
  name: "kt-user-menu",
  components: {},
  setup() {
    const router = useRouter();
    const store = useStore();

    const signOut = () => {
      store
        .dispatch(Actions.LOGOUT)
        .then(() => router.push({ name: "sign-in" }));
    };

    return {
      signOut
    };
  }
});
</script>
