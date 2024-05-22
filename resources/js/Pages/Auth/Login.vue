<script setup>
import GuestLayout from "@/Layouts/GuestLayout.vue";
import { Head, Link, useForm } from "@inertiajs/vue3";
import { ref } from 'vue';

defineProps({
  canResetPassword: {
    type: Boolean,
  },
  status: {
    type: String,
  },
});

const showPassword = ref(false);

const form = useForm({
  email: "",
  password: "",
  remember: false,
});

const submit = () => {
  form.post(route("login"), {
    onFinish: () => form.reset("password"),
  });
};
</script>

<template>
  <GuestLayout>
    <Head title="Log in" />

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
      <div class="card card-md">
        <div class="card-body">
          <h2 class="h2 text-center mb-4">Login to your account</h2>
          <form @submit.prevent="submit">
            <div class="mb-3">
              <label class="form-label">Email address</label>
              <input
                id="email"
                type="email"
                class="form-control"
                :class="{ 'is-invalid': form.errors.email }"
                v-model="form.email"
                required
                autofocus
                autocomplete="username"
                placeholder="your@email.com"
              />
              <div class="invalid-feedback">{{ form.errors.email }}</div>
            </div>
            <div class="mb-2">
              <label class="form-label">
                Password
                <span class="form-label-description">
                  <Link
                    v-if="canResetPassword"
                    :href="route('password.request')"
                  >
                    I forgot password
                  </Link>
                </span>
              </label>
              <div class="input-group input-group-flat">
                <input
                  id="password"
                  :type="[showPassword ? 'text' : 'password']"
                  class="form-control"
                  :class="{ 'is-invalid': form.errors.password }"
                  v-model="form.password"
                  placeholder="Your password"
                  required
                  autocomplete="current-password"
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
            <div class="mb-2">
              <label class="form-check">
                <input
                  type="checkbox"
                  class="form-check-input"
                  name="remember"
                  v-model="form.remember"
                />
                <span class="form-check-label">Remember me on this device</span>
              </label>
            </div>
            <div class="form-footer">
              <button
                type="submit"
                class="btn btn-primary w-100"
                :disabled="form.processing"
              >
                Sign in
              </button>
            </div>
          </form>
        </div>
      </div>
      <div class="text-center text-muted mt-3">
        Don't have account yet?
        <Link :href="route('register')" tabindex="-1">Sign up</Link>
      </div>
    </div>
  </GuestLayout>
</template>
