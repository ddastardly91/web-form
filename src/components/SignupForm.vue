<template>
  <form>
    <label>Email:</label>
    <input
      type="email"
      v-model="email"
      placeholder="example@email.com"
      required
    />

    <label>Password:</label>
    <input type="password" v-model="password" required />

    <label>Role:</label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>

    <label>Skills:</label>
    <input type="text" v-model="tempSkill" @keyup="addSkill" />
    <div class="skill-container">
      <span
        v-for="skill in skills"
        class="pill"
        :key="skill"
        @click="removeSkill(skill)"
        >{{ skill }}</span
      >
    </div>

    <div class="terms">
      <input type="checkbox" v-model="terms" required />
      <label>Accept Terms and Conditions</label>
    </div>

    <div class="submit">
      <button>Create and Account</button>
    </div>
  </form>

  <p>Email: {{ email }}</p>
  <p>Password: {{ password }}</p>
  <p>Role: {{ role }}</p>
  <p>Terms Accepted: {{ terms }}</p>
  <p>{{ skills }}</p>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "developer",
      terms: false,
      tempSkill: "",
      skills: [],
    };
  },

  methods: {
    addSkill(e) {
      if (e.key === "," && this.tempSkill) {
        this.tempSkill = this.tempSkill.replace(",", "");
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill.toLowerCase());
        }
        this.tempSkill = "";
      }
    },

    removeSkill(skill) {
      this.skills = this.skills.filter((item) => item != skill);
    },
  },
};
</script>

<style scoped>
form {
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}

label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}

input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}

input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin: 0 10px 0 0;
  position: relative;
  top: 3px;
}

input[type="checkbox"] {
  accent-color: #42d392;
}

select,
input:focus {
  outline-color: #42d392;
}
.pill {
  background-color: #42d392;
  color: white;
  font-size: 12px;
  padding: 2px 12px;
  border-radius: 25px;
  margin: 5px 5px;
}

.pill:hover {
  background-color: #2dc580;
  cursor: pointer;
}

.skill-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 10px;
}

.submit {
  text-align: center;
}

.submit button {
  background-color: #42d392;
  border: 0;
  font-weight: bold;
  padding: 10px 20px;
  margin-top: 20px;
  color: white;
  border-radius: 20px;
}
</style>
