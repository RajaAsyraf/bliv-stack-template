<script setup>
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
import DeleteUserForm from "./Partials/DeleteUserForm.vue";
import UpdatePasswordForm from "./Partials/UpdatePasswordForm.vue";
import UpdateProfileInformationForm from "./Partials/UpdateProfileInformationForm.vue";
import { Head, useForm, usePage } from "@inertiajs/vue3";

defineProps({
  mustVerifyEmail: {
    type: Boolean,
  },
  status: {
    type: String,
  },
});

const user = usePage().props.auth.user;

const form = useForm({
  name: user.name,
  email: user.email,
});
</script>

<template>
  <Head title="Settings" />

  <AuthenticatedLayout>
    <template #header>
      <h2 class="page-title">Settings</h2>
    </template>

    <div class="card">
      <div class="row g-0">
        <div class="col-3 d-none d-md-block border-end">
          <div class="card-body">
            <h4 class="subheader">Account settings</h4>
            <div class="list-group list-group-transparent">
              <a
                :href="route('profile.edit')"
                class="list-group-item list-group-item-action d-flex align-items-center active"
                >My Account</a
              >
            </div>
          </div>
        </div>
        <div class="col d-flex flex-column">
          <form @submit.prevent="form.patch(route('profile.update'))">
            <div class="card-body">
              <h2 class="mb-4">My Account</h2>
              <!-- <h3 class="card-title">Profile Photo</h3>
              <div class="row align-items-center">
                <div class="col-auto">
                  <span
                    class="avatar avatar-xl"
                    style="background-image: url(./static/avatars/000m.jpg)"
                  ></span>
                </div>
                <div class="col-auto">
                  <a href="javascript:void(0);" class="btn"> Change avatar </a>
                </div>
                <div class="col-auto">
                  <a href="javascript:void(0);" class="btn btn-ghost-danger"> Delete avatar </a>
                </div>
              </div> -->
              <h3 class="card-title mt-4">Profile Details</h3>
              <p class="card-subtitle">
                Update your account's profile information and email address.
              </p>
              <div class="row g-3">
                <div class="col-md-6">
                  <div class="form-label">Name</div>
                  <input
                    id="name"
                    type="text"
                    class="form-control"
                    v-model="form.name"
                    required
                    autofocus
                    autocomplete="name"
                  />
                </div>
              </div>
              <h3 class="card-title mt-4">Email</h3>
              <div>
                <div class="row">
                  <div class="col-md-6">
                    <input
                      class="form-control"
                      id="email"
                      type="email"
                      v-model="form.email"
                      required
                      autocomplete="username"
                    />
                  </div>
                </div>
              </div>
              <h3 class="card-title mt-4">Password</h3>
              <p class="card-subtitle">
                Ensure your account is using a long, random password to stay
                secure.
              </p>
              <div>
                <a href="javascript:void(0);" class="btn" data-bs-toggle="modal" data-bs-target="#set-password">
                    Set new password
                  </a>
              </div>
              <h3 class="card-title mt-4">Delete Account</h3>
              <p class="card-subtitle">
                Once your account is deleted, all of its resources and data will
                be permanently deleted. Before deleting your account, please
                download any data or information that you wish to retain.
              </p>
              <div>
                <a href="javascript:void(0);" class="btn btn-danger"> Delete Account </a>
              </div>
            </div>
            <div class="card-footer bg-transparent mt-auto">
              <div class="btn-list justify-content-end">
                <button class="btn btn-primary" :disabled="form.processing">
                  Submit
                </button>
              </div>
            </div>
          </form>
        </div>
      </div>
    </div>

    <UpdatePasswordForm/>
  </AuthenticatedLayout>
</template>
