<script setup>
import InputError from "@/Components/InputError.vue";
import InputLabel from "@/Components/InputLabel.vue";
import PrimaryButton from "@/Components/PrimaryButton.vue";
import TextInput from "@/Components/TextInput.vue";
import { useForm } from "@inertiajs/vue3";
import { ref } from "vue";

const passwordInput = ref(null);
const currentPasswordInput = ref(null);
const showCurrentPassword = ref(false);
const showNewPassword = ref(false);
const showPasswordConfirmation = ref(false);

const form = useForm({
  current_password: "",
  password: "",
  password_confirmation: "",
});

const updatePassword = () => {
  form.put(route("password.update"), {
    preserveScroll: true,
    onSuccess: () => form.reset(),
    onError: () => {
      if (form.errors.password) {
        form.reset("password", "password_confirmation");
        passwordInput.value.focus();
      }
      if (form.errors.current_password) {
        form.reset("current_password");
        currentPasswordInput.value.focus();
      }
    },
  });
};
</script>

<template>
  <section>
    <div
      class="modal modal-blur fade"
      id="set-password"
      tabindex="-1"
      role="dialog"
      aria-hidden="true"
    >
      <div class="modal-dialog modal-dialog-centered" role="document">
        <div class="modal-content">
          <form @submit.prevent="updatePassword">
            <div class="modal-header">
              <h5 class="modal-title">Set new password</h5>
              <button
                type="button"
                class="btn-close"
                data-bs-dismiss="modal"
                aria-label="Close"
              ></button>
            </div>
            <div class="modal-body">
              <div class="mb-3">
                <label class="form-label">Current Password</label>
                <div
                  class="input-group input-group-flat"
                  :class="{ 'is-invalid': form.errors.current_password }"
                >
                  <input
                    class="form-control"
                    :class="{ 'is-invalid': form.errors.current_password }"
                    placeholder="Current password"
                    required
                    autofocus
                    id="current_password"
                    ref="currentPasswordInput"
                    v-model="form.current_password"
                    :type="[showCurrentPassword ? 'text' : 'password']"
                    autocomplete="current-password"
                  />
                  <span class="input-group-text">
                    <a
                      href="javascript:void(0);"
                      class="link-secondary"
                      title="Show password confirmation"
                      data-bs-toggle="tooltip"
                      @click="showCurrentPassword = !showCurrentPassword"
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
                </div>
                <div class="invalid-feedback">
                  {{ form.errors.current_password }}
                </div>
              </div>
              <div class="mb-3">
                <label class="form-label">New Password</label>
                <div
                  class="input-group input-group-flat"
                  :class="{ 'is-invalid': form.errors.password }"
                >
                  <input
                    class="form-control"
                    :class="{ 'is-invalid': form.errors.password }"
                    placeholder="New password"
                    required
                    autofocus
                    id="password"
                    ref="passwordInput"
                    v-model="form.password"
                    :type="[showNewPassword ? 'text' : 'password']"
                    autocomplete="new-password"
                  />
                  <span class="input-group-text">
                    <a
                      href="javascript:void(0);"
                      class="link-secondary"
                      title="Show password confirmation"
                      data-bs-toggle="tooltip"
                      @click="showNewPassword = !showNewPassword"
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
                </div>
                <div class="invalid-feedback">{{ form.errors.password }}</div>
              </div>
              <div class="mb-3">
                <label class="form-label">Confirm Password</label>
                <div
                  class="input-group input-group-flat"
                  :class="{ 'is-invalid': form.errors.password_confirmation }"
                >
                  <input
                    class="form-control"
                    :class="{ 'is-invalid': form.errors.password_confirmation }"
                    placeholder="Confirm password"
                    required
                    autofocus
                    id="password_confirmation"
                    v-model="form.password_confirmation"
                    :type="[showPasswordConfirmation ? 'text' : 'password']"
                    autocomplete="new-password"
                  />
                  <span class="input-group-text">
                    <a
                      href="javascript:void(0);"
                      class="link-secondary"
                      title="Show password confirmation"
                      data-bs-toggle="tooltip"
                      @click="
                        showPasswordConfirmation = !showPasswordConfirmation
                      "
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
                </div>
                <div class="invalid-feedback">
                  {{ form.errors.password_confirmation }}
                </div>
              </div>
            </div>
            <div class="modal-footer">
              <button type="button" class="btn me-auto" data-bs-dismiss="modal">
                Close
              </button>
              <button class="btn btn-primary" :disabled="form.processing">
                Save
              </button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>
