<script setup>
import { ref, watch } from "vue";
import { onMounted } from "vue";
import validator from "validator";

const usernameRef = ref(null);

const username = ref("");
const password = ref("");
const password2 = ref("");
const email = ref("");
const phone = ref("");
const disabled = ref(true);

const validUsername = ref(false);
const validPassword = ref(false);
const passwordsMatch = ref(false);
const validEmail = ref(false);
const validPhoneNum = ref(false);

const usernameErrorRef = ref(null);
const passwordErrorRef = ref(null);
const password2ErrorRef = ref(null);
const emailErrorRef = ref(null);
const phoneErrorRef = ref(null);

// watch element ref - similar to onMounted - not watching value of input
// for some reason disabled when ref function is installed
let count = 0;
watch(usernameRef, () => {
  console.log("watching usernameRef");
  console.log(usernameRef.value);
  console.log(count++);
});

// called when anything in component changes - including onMounted
// if used in input element, must have v-model set
function componentUpdate(elm) {
  console.log("password changed");
  console.log(elm.value);
  console.log(passwordErrorRef.value);

  if (passwordErrorRef.value != null && elm.value.length > 0) {
    validPassword.value = elm.value.length >= 8;

    passwordErrorRef.value.innerHTML = validPassword.value
      ? "&nbsp;"
      : "Minimum length: 8 characters";
  }
}

//watch v-model input.value ref (called when string changes)
watch(username, () => {
  validUsername.value = username.value.length >= 4;

  usernameErrorRef.value.innerHTML = validUsername.value
    ? "&nbsp;"
    : "Minimum length: 4 characters";
});

// watch array of refs
watch([password, password2], () => {
  passwordsMatch.value = password.value === password2.value;

  password2ErrorRef.value.innerHTML =
    passwordsMatch.value || password2.value.length == 0
      ? "&nbsp;"
      : "Passwords do not match";
});

watch(email, () => {
  validEmail.value = validator.isEmail(email.value);

  emailErrorRef.value.innerHTML = validEmail.value
    ? "&nbsp;"
    : "Please enter a valid email";
});

watch(phone, () => {
  validPhoneNum.value = validator.isMobilePhone(phone.value);

  phoneErrorRef.value.innerHTML = validPhoneNum.value
    ? "&nbsp;"
    : "Please enter a valid phone number";
});

function loadPreviewImg(event) {
  let reader = new FileReader();

  reader.onloadend = function () {
    let img = document.querySelector("#preview-img");
    img.src = reader.result;
  };

  reader.readAsDataURL(event.target.files[0]);
}

// watch array of refs
watch(
  [validUsername, validPassword, passwordsMatch, validEmail, validPhoneNum],
  async () => {
    disabled.value = !(
      validUsername.value &&
      validPassword.value &&
      passwordsMatch.value &&
      validEmail.value &&
      validPhoneNum.value
    );

    if (!disabled.value) usernameRef.value.value = "";
  }
);

function submit() {
  let mssg = username.value + ", " + password.value;
  console.log(mssg);
}

onMounted(() => {
  usernameRef.value.focus();
});
</script>

<template>
  <div class="container">
    <form class="rounded border border-primary border-2 border-opacity-25 py-3 px-5">
      <fieldset class="d-flex flex-column">
        <legend>Create Account</legend>

        <div class="form-floating mb-2">
          <input
            ref="usernameRef"
            v-model="username"
            id="username"
            type="text"
            class="form-control"
          />
          <label for="username" class="form-label">Username</label>
          <small ref="usernameErrorRef" class="text-danger">&nbsp</small>
        </div>

        <div class="form-floating mb-2">
          <input
            :ref="componentUpdate"
            v-model="password"
            id="password"
            type="password"
            class="form-control"
          />
          <label for="password" class="form-label">Password</label>
          <small ref="passwordErrorRef" class="text-danger">&nbsp;</small>
        </div>

        <div class="form-floating mb-2">
          <input
            v-model="password2"
            id="password2"
            type="password"
            class="form-control"
          />
          <label for="password2" class="form-label">Reenter password</label>
          <small ref="password2ErrorRef" class="text-danger">&nbsp;</small>
        </div>

        <div class="form-floating mb-2">
          <input v-model="email" id="email" type="email" class="form-control" />
          <label for="email" class="form-label">Email</label>
          <small ref="emailErrorRef" class="text-danger">&nbsp;</small>
        </div>

        <div class="form-floating mb-2">
          <input v-model="phone" id="phone" type="phone" class="form-control" />
          <label for="phone" class="form-label">Phone Number</label>
          <small ref="phoneErrorRef" class="text-danger">&nbsp;</small>
        </div>

        <div class="form-floating mb-2">
          <input
            @change="loadPreviewImg"
            id="profilePic"
            type="file"
            accept="image/png, image/jpeg"
            class="form-control"
          />
          <label for="profilePic" id="img-label" class="form-label"
            >Banner Picture (optional)</label
          >
          <img id="preview-img" />
        </div>

        <div>
          <button
            @click="submit"
            class="btn btn-primary"
            type="button"
            v-bind:disabled="disabled"
          >
            Create
          </button>
        </div>
      </fieldset>
    </form>
  </div>
</template>

<style>
#img-label {
  padding: 5px;
}

#preview-img {
  margin: 10px;
  width: 500px;
  border: #2d3962 solid 2px;
}
</style>
