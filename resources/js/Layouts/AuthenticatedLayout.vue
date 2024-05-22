<script setup>
import { ref } from "vue";
import { useForm } from "@inertiajs/vue3";

const showingNavigationDropdown = ref(false);

const logout = () => {
  useForm({}).post(route("logout"));
};
</script>

<template>
  <div class="page">
    <!-- Navbar -->
    <header class="navbar navbar-expand-md d-print-none">
      <div class="container-xl">
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbar-menu"
          aria-controls="navbar-menu"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <h1
          class="navbar-brand navbar-brand-autodark d-none-navbar-horizontal pe-0 pe-md-3"
        >
          <a href=".">
            <img
              src="https://preview.tabler.io/static/logo.svg"
              width="110"
              height="32"
              alt="Tabler"
              class="navbar-brand-image"
            />
          </a>
        </h1>
        <div class="navbar-nav flex-row order-md-last">
          <div class="d-none d-md-flex">
            <a
              href="?theme=dark"
              class="nav-link px-0 hide-theme-dark"
              title="Enable dark mode"
              data-bs-toggle="tooltip"
              data-bs-placement="bottom"
            >
              <!-- Download SVG icon from http://tabler-icons.io/i/moon -->
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
                  d="M12 3c.132 0 .263 0 .393 0a7.5 7.5 0 0 0 7.92 12.446a9 9 0 1 1 -8.313 -12.454z"
                />
              </svg>
            </a>
            <a
              href="?theme=light"
              class="nav-link px-0 hide-theme-light"
              title="Enable light mode"
              data-bs-toggle="tooltip"
              data-bs-placement="bottom"
            >
              <!-- Download SVG icon from http://tabler-icons.io/i/sun -->
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
                <path d="M12 12m-4 0a4 4 0 1 0 8 0a4 4 0 1 0 -8 0" />
                <path
                  d="M3 12h1m8 -9v1m8 8h1m-9 8v1m-6.4 -15.4l.7 .7m12.1 -.7l-.7 .7m0 11.4l.7 .7m-12.1 -.7l-.7 .7"
                />
              </svg>
            </a>
            <div class="nav-item dropdown d-none d-md-flex me-3">
              <a
                href="#"
                class="nav-link px-0"
                data-bs-toggle="dropdown"
                tabindex="-1"
                aria-label="Show notifications"
              >
                <!-- Download SVG icon from http://tabler-icons.io/i/bell -->
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
                    d="M10 5a2 2 0 1 1 4 0a7 7 0 0 1 4 6v3a4 4 0 0 0 2 3h-16a4 4 0 0 0 2 -3v-3a7 7 0 0 1 4 -6"
                  />
                  <path d="M9 17v1a3 3 0 0 0 6 0v-1" />
                </svg>
                <span class="badge bg-red"></span>
              </a>
              <div
                class="dropdown-menu dropdown-menu-arrow dropdown-menu-end dropdown-menu-card"
              >
                <div class="card">
                  <div class="card-header">
                    <h3 class="card-title">Last updates</h3>
                  </div>
                  <div class="list-group list-group-flush list-group-hoverable">
                    <div class="list-group-item">
                      <div class="row align-items-center">
                        <div class="col-auto">
                          <span
                            class="status-dot status-dot-animated bg-red d-block"
                          ></span>
                        </div>
                        <div class="col text-truncate">
                          <a href="#" class="text-body d-block">Example 1</a>
                          <div class="d-block text-muted text-truncate mt-n1">
                            Change deprecated html tags to text decoration
                            classes (#29604)
                          </div>
                        </div>
                        <div class="col-auto">
                          <a href="#" class="list-group-item-actions">
                            <!-- Download SVG icon from http://tabler-icons.io/i/star -->
                            <svg
                              xmlns="http://www.w3.org/2000/svg"
                              class="icon text-muted"
                              width="24"
                              height="24"
                              viewBox="0 0 24 24"
                              stroke-width="2"
                              stroke="currentColor"
                              fill="none"
                              stroke-linecap="round"
                              stroke-linejoin="round"
                            >
                              <path
                                stroke="none"
                                d="M0 0h24v24H0z"
                                fill="none"
                              />
                              <path
                                d="M12 17.75l-6.172 3.245l1.179 -6.873l-5 -4.867l6.9 -1l3.086 -6.253l3.086 6.253l6.9 1l-5 4.867l1.179 6.873z"
                              />
                            </svg>
                          </a>
                        </div>
                      </div>
                    </div>
                    <div class="list-group-item">
                      <div class="row align-items-center">
                        <div class="col-auto">
                          <span class="status-dot d-block"></span>
                        </div>
                        <div class="col text-truncate">
                          <a href="#" class="text-body d-block">Example 2</a>
                          <div class="d-block text-muted text-truncate mt-n1">
                            justify-content:between ⇒
                            justify-content:space-between (#29734)
                          </div>
                        </div>
                        <div class="col-auto">
                          <a href="#" class="list-group-item-actions show">
                            <!-- Download SVG icon from http://tabler-icons.io/i/star -->
                            <svg
                              xmlns="http://www.w3.org/2000/svg"
                              class="icon text-yellow"
                              width="24"
                              height="24"
                              viewBox="0 0 24 24"
                              stroke-width="2"
                              stroke="currentColor"
                              fill="none"
                              stroke-linecap="round"
                              stroke-linejoin="round"
                            >
                              <path
                                stroke="none"
                                d="M0 0h24v24H0z"
                                fill="none"
                              />
                              <path
                                d="M12 17.75l-6.172 3.245l1.179 -6.873l-5 -4.867l6.9 -1l3.086 -6.253l3.086 6.253l6.9 1l-5 4.867l1.179 6.873z"
                              />
                            </svg>
                          </a>
                        </div>
                      </div>
                    </div>
                    <div class="list-group-item">
                      <div class="row align-items-center">
                        <div class="col-auto">
                          <span class="status-dot d-block"></span>
                        </div>
                        <div class="col text-truncate">
                          <a href="#" class="text-body d-block">Example 3</a>
                          <div class="d-block text-muted text-truncate mt-n1">
                            Update change-version.js (#29736)
                          </div>
                        </div>
                        <div class="col-auto">
                          <a href="#" class="list-group-item-actions">
                            <!-- Download SVG icon from http://tabler-icons.io/i/star -->
                            <svg
                              xmlns="http://www.w3.org/2000/svg"
                              class="icon text-muted"
                              width="24"
                              height="24"
                              viewBox="0 0 24 24"
                              stroke-width="2"
                              stroke="currentColor"
                              fill="none"
                              stroke-linecap="round"
                              stroke-linejoin="round"
                            >
                              <path
                                stroke="none"
                                d="M0 0h24v24H0z"
                                fill="none"
                              />
                              <path
                                d="M12 17.75l-6.172 3.245l1.179 -6.873l-5 -4.867l6.9 -1l3.086 -6.253l3.086 6.253l6.9 1l-5 4.867l1.179 6.873z"
                              />
                            </svg>
                          </a>
                        </div>
                      </div>
                    </div>
                    <div class="list-group-item">
                      <div class="row align-items-center">
                        <div class="col-auto">
                          <span
                            class="status-dot status-dot-animated bg-green d-block"
                          ></span>
                        </div>
                        <div class="col text-truncate">
                          <a href="#" class="text-body d-block">Example 4</a>
                          <div class="d-block text-muted text-truncate mt-n1">
                            Regenerate package-lock.json (#29730)
                          </div>
                        </div>
                        <div class="col-auto">
                          <a href="#" class="list-group-item-actions">
                            <!-- Download SVG icon from http://tabler-icons.io/i/star -->
                            <svg
                              xmlns="http://www.w3.org/2000/svg"
                              class="icon text-muted"
                              width="24"
                              height="24"
                              viewBox="0 0 24 24"
                              stroke-width="2"
                              stroke="currentColor"
                              fill="none"
                              stroke-linecap="round"
                              stroke-linejoin="round"
                            >
                              <path
                                stroke="none"
                                d="M0 0h24v24H0z"
                                fill="none"
                              />
                              <path
                                d="M12 17.75l-6.172 3.245l1.179 -6.873l-5 -4.867l6.9 -1l3.086 -6.253l3.086 6.253l6.9 1l-5 4.867l1.179 6.873z"
                              />
                            </svg>
                          </a>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="nav-item dropdown">
            <a
              href="#"
              class="nav-link d-flex lh-1 text-reset p-0"
              data-bs-toggle="dropdown"
              aria-label="Open user menu"
            >
              <span
                class="avatar avatar-sm"
                style="
                  background-image: url('data:image/jpeg;base64,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');
                "
              ></span>
              <div class="d-none d-xl-block ps-2">
                <div>{{ $page.props.auth.user.name }}</div>
                <div class="mt-1 small text-muted">{{ $page.props.auth.user.email }}</div>
              </div>
            </a>
            <div class="dropdown-menu dropdown-menu-end dropdown-menu-arrow">
              <a :href="route('profile.edit')" class="dropdown-item">Settings</a>
              <form @submit.prevent="logout">
                <button class="dropdown-item">Logout</button>
              </form>
            </div>
          </div>
        </div>
      </div>
    </header>
    <!-- Menu -->
    <header class="navbar-expand-md">
      <div class="navbar-collapse" id="navbar-menu">
        <div class="navbar">
          <div class="container-xl">
            <ul class="navbar-nav">
              <li class="nav-item">
                <a class="nav-link" href="./">
                  <span class="nav-link-icon d-md-none d-lg-inline-block"
                    ><!-- Download SVG icon from http://tabler-icons.io/i/home -->
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
                      <path d="M5 12l-2 0l9 -9l9 9l-2 0" />
                      <path d="M5 12v7a2 2 0 0 0 2 2h10a2 2 0 0 0 2 -2v-7" />
                      <path d="M9 21v-6a2 2 0 0 1 2 -2h2a2 2 0 0 1 2 2v6" />
                    </svg>
                  </span>
                  <span class="nav-link-title"> Dashboard </span>
                </a>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </header>
    <div class="page-wrapper">
      <!-- Page header -->
      <div class="page-header d-print-none">
        <div class="container-xl">
          <div class="row g-2 align-items-center">
            <div class="col">
              <slot name="header" />
            </div>
          </div>
        </div>
      </div>
      <!-- Page body -->
      <div class="page-body">
        <div class="container-xl">
          <main>
            <slot />
          </main>
        </div>
      </div>
      <!-- Page footer -->
      <footer class="footer footer-transparent d-print-none">
        <div class="container-xl">
          <div class="row text-center align-items-center flex-row-reverse">
            <div class="col-lg-auto ms-lg-auto">
              <ul class="list-inline list-inline-dots mb-0">
                <li class="list-inline-item"></li>
              </ul>
            </div>
            <div class="col-12 col-lg-auto mt-3 mt-lg-0">
              <ul class="list-inline list-inline-dots mb-0">
                <li class="list-inline-item">
                  Copyright © 2024 RentProps. All rights reserved.
                </li>
              </ul>
            </div>
          </div>
        </div>
      </footer>
    </div>
  </div>
</template>
