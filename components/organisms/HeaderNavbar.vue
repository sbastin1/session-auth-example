<template>
  <nav class="container">
    <ul class="container__list">
      <li class="container__list__dropdown">
        <button @click="toggleDropdown">
          <NuxtImg
            src="/icons/arrow.svg"
            height="20"
            width="20"
            :class="{ 'arrow-transition': dropdownState }"
          />
          Menu
        </button>
        <ul
          class="container__list__dropdown__items"
          :class="{ 'dropdown-visibility': !dropdownState }"
        >
          <li><NuxtLink to="/">Home</NuxtLink></li>
          <li><NuxtLink to="/protected">Protected Page</NuxtLink></li>
        </ul>
      </li>
      <ul class="container__list__redirects">
        <li class="container__list__redirects__login">
          <NuxtLink to="/login">Login</NuxtLink>
        </li>
        <li class="container__list__redirects__signup">
          <NuxtLink to="/signup">Sign Up</NuxtLink>
        </li>
      </ul>
    </ul>
  </nav>
</template>

<script setup lang="ts">
const dropdownState = ref(false);

const toggleDropdown = () => {
  dropdownState.value = !dropdownState.value;
};
</script>

<style scoped lang="scss">
.container {
  padding: 20px;

  a {
    text-decoration: none;
    color: inherit;
  }

  ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
  }

  &__list {
    display: flex;
    justify-content: space-between;
    font-size: 1.3rem;

    &__dropdown {
      button {
        background-color: $primary_accent;
        border: 0;
        padding: 10px;
        border-radius: 4px;
        font-size: 1.3rem;
        cursor: pointer;
        display: flex;
        align-items: center;
        gap: 8px;

        .arrow-transition {
          transform: rotate(0deg);
        }
        img {
          transform: rotate(180deg);
          transition: transform 0.4s ease-in-out;
        }

        @media only screen and (min-width: 720px) {
          display: none;
        }
      }

      .dropdown-visibility {
        display: none;
      }

      &__items {
        position: absolute;
        background-color: rgb(59, 59, 59);
        border-radius: 0 4px 4px 4px;
        li {
          margin: 10px 0;
          padding: 8px;

          &:hover {
            background-color: rgb(49, 49, 49);
          }

          @media only screen and (min-width: 720px) {
            &:hover {
              border-radius: 6px;
            }
          }
        }

        /* Important Tag neccesary to display navbar when manually resizing window */
        @media only screen and (min-width: 720px) {
          position: initial;
          display: flex !important;
          background-color: unset;
          gap: 60px;
        }
      }
    }

    &__redirects {
      display: flex;
      justify-content: flex-end;
      align-items: center;
      gap: 40px;

      &__signup {
        a {
          background-color: $primary_accent;
          color: black;
          padding: 10px;
          border-radius: 4px;

          &:hover {
            background-color: $primary_hover;
          }
        }
      }

      &__login {
        a {
          padding: 8px;
          border-radius: 6px;
          &:hover {
            background-color: rgb(49, 49, 49);
          }
        }
      }
    }
  }
}
</style>
