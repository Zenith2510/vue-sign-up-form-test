<template>
  <form @submit.prevent="submit">
    <label for="email">Email</label><br />
    <input type="email" id="email" v-model="email" /><br />
    <label for="username">User Name</label><br />
    <input type="text" v-model="userName" /><br />
    <label for="username">Password</label><br />
    <input type="password" v-model="password" /><br />
    <div>
      <small v-if="errorMsg" style="color: red">{{ errorMsg }}</small>
    </div>
    <select style="margin: 20px 0px">
      <option value="">Please Select Role</option>
      <option value="dev">Developer</option>
      <option value="des">Designer</option>
    </select>
    <br />
    <label for="">Skills</label><br />
    <input type="text" id v-model="skill" @keyup="addSkill" /><br />
    <!-- <button>Reset</button> -->

    <div v-for="skill in skills" :key="skill">
      <p>
        {{ skill }} <span class="cross" @click="delSkill(skill)">&#10060;</span>
      </p>
    </div>
    <br />
    <!-- <button :v-model="(skills = '')">Reset</button> -->

    <div>
      <input type="checkbox" v-model="accept" />
      <label style="margin-left: 5px" for="">accept terms</label><br />
    </div>
    <button>Create</button>
    <!-- <div>
      <div>
        <label for="">name - 1</label>
        <input type="checkbox" value="1" v-model="names" />
      </div>
      <div>
        <label for="">name - 2</label>
        <input type="checkbox" value="2" v-model="names" />
      </div>
      <div>
        <label for="">name - 3</label>
        <input type="checkbox" value="3" v-model="names" />
      </div>
    </div> -->

    <!-- <p>names - {{ names.toString() }}</p> -->
  </form>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      userName: "",
      password: "",
      accept: false,
      names: [],
      skills: [],
      skill: "",
      errorMsg: "",
    };
  },
  methods: {
    // addSkill(e) {
    //   if (e.key === " ") {
    //     this.skills.push(this.skill);
    //     this.skill = "";
    //   }
    // },
    addSkill(e) {
      if (e.key === " " && this.skill.trim() !== "") {
        this.skills.push(this.skill.trim());
        this.skill = "";
      }
    },
    delSkill(skill) {
      // this.skill;
      // console.log(skill);
      this.skills = this.skills.filter((loopSkill) => loopSkill != skill);
    },
    submit() {
      if (this.password.length < 8) {
        this.errorMsg = "password must be atleast 8 characters";
      }
      //  else if (this.password != ) {
      //   this.errorMsg = "use strinng";
      // }
    },
  },
};
</script>

<style>
* {
  color: black;
}
.cross {
  cursor: pointer;
}
</style>
