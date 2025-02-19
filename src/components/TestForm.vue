<template>
  <v-sheet class="mx-auto" width="300">
    <p>tutaj -- {{ valid }}</p>
    <v-form @submit.prevent="handleSubmit" v-model="valid">
      <v-text-field
        v-model="login"
        :rules="rules.login"
        label="Login"
      ></v-text-field>
      <v-text-field
        v-model="password"
        :rules="rules.password"
        type="password"
        validate-on="blur"
        label="Password"
      ></v-text-field>
      <v-btn class="mt-2" type="submit" block>Submit</v-btn>
    </v-form>
    <v-btn class="mt-2" color="primary" block>Submit</v-btn>
    <v-btn class="mt-2" color="green-lighten-5" block>Submit</v-btn>
  </v-sheet>
</template>

<script lang="ts" setup>
const valid = ref(false);
const login = ref("");
const password = ref("");
const rules = {
  login: [(value: string) => !!value || "Required."],
  password: [(value: string) => value.length >= 6 || "Min 6 characters."],
};

const handleSubmit = () => {
  if (!valid.value) return;
  console.log(login.value, valid.value);
};
</script>
