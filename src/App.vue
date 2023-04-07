<template>
  <div class="container">
    <form @submit="validateForm">
      <div class="formRow">
        <label for="">Username</label>
        <input
          :class="errors.username && 'input-error'"
          type="text"
          name="username"
          v-model="username"
        />
        <span v-if="errors.username" :class="errors.username && 'error'">{{
          errors.username
        }}</span>
      </div>
      <div class="formRow">
        <label for="">Subject</label>
        <input
          :class="errors.subject && 'input-error'"
          type="text"
          name="subject"
          v-model="subject"
        />
        <span v-if="errors.subject" :class="errors.subject && 'error'">{{
          errors.subject
        }}</span>
      </div>

      <div class="formRow">
        <button>Submit</button>
      </div>
    </form>
  </div>
</template>

<script type="text/javascript">
export default {
  data() {
    return {
      errors: {},
      username: null,
      subject: null,
    };
  },
  methods: {
    validateForm(e) {
      this.errors = {};

      //check if username is empty
      if (!this.username) {
        this.errors.username = "Username is required";
      }

      //check if subject is empty
      if (!this.subject) {
        this.errors.subject = "Subject is required";
      }

      e.preventDefault();
    },
  },
};
</script>

<style lang="scss">
*,
*::after,
*::before {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  list-style: none;
}

body {
  font-family: 62.5%;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  height: 100vh;
  background: #e6e7e5;
  display: flex;
  justify-content: center;
}

.container {
  margin-top: 7rem;
  padding: 3rem;
  width: 600px;
  border-radius: 4px;
}

form {
  border: 2px solid rgba(29, 53, 87);
  padding: 2rem;
  border-radius: 4px;
  box-shadow: 0 0 #0000, 0 25px 50px -12px rgba(0, 0, 0, 0.25), 0 0 #0000;
  background: white;
}

.formRow {
  display: flex;
  flex-direction: column;
  margin-bottom: 1.5rem;
}

label,
input {
  color: #293241;
}

label {
  font-size: 1.2rem;
  margin-bottom: 0.5rem;
}

input {
  border: 2px solid rgba(#1d3557, 0.8);
  border-radius: 4px;
  padding: 0.5rem 1rem;
  padding-left: 1rem;
  font-size: 1rem;
}

.input-error {
  border-color: #e63946;
}

.error {
  color: #e63946;
  font-size: 1rem;
  margin-top: 0.3rem;
}

button {
  color: #fff;
  width: 100%;
  font-size: 1.4rem;
  background: #1d3557;
  border-radius: 4px;
  border: none;
  cursor: pointer;
  padding: 0.8rem 1.2rem;
  margin-top: 0.5rem;
}
</style>
