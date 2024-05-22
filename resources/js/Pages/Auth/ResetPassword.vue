<script setup>
import GuestLayout from "@/Layouts/GuestLayout.vue";
import { Head, useForm } from "@inertiajs/vue3";
import { ref } from "vue";

const props = defineProps({
  email: {
    type: String,
    required: true,
  },
  token: {
    type: String,
    required: true,
  },
});

const form = useForm({
  token: props.token,
  email: props.email,
  password: "",
  password_confirmation: "",
});

const showPassword = ref(false);
const showConfirmPassword = ref(false);

const submit = () => {
  form.post(route("password.store"), {
    onFinish: () => form.reset("password", "password_confirmation"),
  });
};
</script>

<template>
  <GuestLayout>
    <Head title="Reset Password" />

    <div class="container container-tight py-4">
      <div class="text-center mb-4">
        <a :href="route('login')" class="navbar-brand navbar-brand-autodark">
          <img
            src="https://preview.tabler.io/static/logo.svg"
            width="110"
            height="32"
            alt="Tabler"
            class="navbar-brand-image"
          />
        </a>
      </div>
      <div v-if="status" class="alert alert-success" role="alert">
        {{ status }}
      </div>
      <form class="card card-md" @submit.prevent="submit">
        <div class="card-body">
          <h2 class="card-title text-center mb-4">Reset password</h2>
          <div class="mb-3">
            <label class="form-label">Email address</label>
            <input
              type="email"
              class="form-control"
              :class="{ 'is-invalid': form.errors.email }"
              placeholder="Enter email"
              id="email"
              v-model="form.email"
              required
              autofocus
              autocomplete="username"
            />
            <div class="invalid-feedback">{{ form.errors.email }}</div>
          </div>
          <div class="mb-3">
            <label class="form-label">Password</label>
            <div class="input-group input-group-flat">
              <input
                :type="[showPassword ? 'text' : 'password']"
                class="form-control"
                :class="{ 'is-invalid': form.errors.password }"
                placeholder="Password"
                id="password"
                v-model="form.password"
                required
                autocomplete="new-password"
              />
              <span class="input-group-text">
                <a
                  href="javascript:void(0);"
                  class="link-secondary"
                  title="Show password"
                  data-bs-toggle="tooltip"
                  @click="showPassword = !showPassword"
                  ><!-- Download SVG icon from http://tabler-icons.io/i/eye -->
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    class="icon"
                    width="24"
                    height="24"
                    viewBox="0 0 24 24"
                    stroke-width="2"
                    stroke="currentColor"
                    fill="none"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                  >
                    <path stroke="none" d="M0 0h24v24H0z" fill="none" />
                    <path d="M10 12a2 2 0 1 0 4 0a2 2 0 0 0 -4 0" />
                    <path
                      d="M21 12c-2.4 4 -5.4 6 -9 6c-3.6 0 -6.6 -2 -9 -6c2.4 -4 5.4 -6 9 -6c3.6 0 6.6 2 9 6"
                    />
                  </svg>
                </a>
              </span>
              <div class="invalid-feedback">{{ form.errors.password }}</div>
            </div>
          </div>
          <div class="mb-3">
            <label class="form-label">Confirm Password</label>
            <div class="input-group input-group-flat">
              <input
                :type="[showConfirmPassword ? 'text' : 'password']"
                class="form-control"
                :class="{ 'is-invalid': form.errors.password_confirmation }"
                placeholder="Confirm Password"
                id="password_confirmation"
                v-model="form.password_confirmation"
                required
                autocomplete="new-password"
              />
              <span class="input-group-text">
                <a
                  href="javascript:void(0);"
                  class="link-secondary"
                  title="Show password"
                  data-bs-toggle="tooltip"
                  @click="showConfirmPassword = !showConfirmPassword"
                  ><!-- Download SVG icon from http://tabler-icons.io/i/eye -->
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    class="icon"
                    width="24"
                    height="24"
                    viewBox="0 0 24 24"
                    stroke-width="2"
                    stroke="currentColor"
                    fill="none"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                  >
                    <path stroke="none" d="M0 0h24v24H0z" fill="none" />
                    <path d="M10 12a2 2 0 1 0 4 0a2 2 0 0 0 -4 0" />
                    <path
                      d="M21 12c-2.4 4 -5.4 6 -9 6c-3.6 0 -6.6 -2 -9 -6c2.4 -4 5.4 -6 9 -6c3.6 0 6.6 2 9 6"
                    />
                  </svg>
                </a>
              </span>
              <div class="invalid-feedback">
                {{ form.errors.password_confirmation }}
              </div>
            </div>
          </div>
          <div class="form-footer">
            <button class="btn btn-primary w-100">
              <!-- Download SVG icon from http://tabler-icons.io/i/mail -->
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="icon"
                width="24"
                height="24"
                viewBox="0 0 24 24"
                stroke-width="2"
                stroke="currentColor"
                fill="none"
                stroke-linecap="round"
                stroke-linejoin="round"
              >
                <path stroke="none" d="M0 0h24v24H0z" fill="none" />
                <path
                  d="M3 7a2 2 0 0 1 2 -2h14a2 2 0 0 1 2 2v10a2 2 0 0 1 -2 2h-14a2 2 0 0 1 -2 -2v-10z"
                />
                <path d="M3 7l9 6l9 -6" />
              </svg>
              Reset Password
            </button>
          </div>
        </div>
      </form>
    </div>
  </GuestLayout>
</template>
