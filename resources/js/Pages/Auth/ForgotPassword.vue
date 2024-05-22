<script setup>
import GuestLayout from "@/Layouts/GuestLayout.vue";
import { Head, useForm } from "@inertiajs/vue3";

defineProps({
  status: {
    type: String,
  },
});

const form = useForm({
  email: "",
});

const submit = () => {
  form.post(route("password.email"));
};
</script>

<template>
  <GuestLayout>
    <Head title="Forgot Password" />

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
          <h2 class="card-title text-center mb-4">Forgot password</h2>
          <p class="text-muted mb-4">
            Enter your email address and your password will be reset and emailed
            to you.
          </p>
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
              Send me new password
            </button>
          </div>
        </div>
      </form>
      <div class="text-center text-muted mt-3">
        Forget it, <a :href="route('login')">send me back</a> to the sign in
        screen.
      </div>
    </div>
  </GuestLayout>
</template>
