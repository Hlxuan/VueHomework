<template>
  <div>
    <form>
      <table>
        <tr>
          <td>Name:</td>
          <td><input type="text" v-model="name" /></td>
        </tr>
        <tr>
          <td>Gender:</td>
          <td>
            <input
              type="radio"
              id="Female"
              value="Female"
              name="gender"
              checked
              v-model="gender"
            />
            <label for="Female">Female</label>
            <input
              type="radio"
              id="Male"
              value="Male"
              name="gender"
              v-model="gender"
            />
            <label for="Male">Male</label>
          </td>
        </tr>
        <tr>
          <td>Year:</td>
          <td>
            <select name="year" id="year" v-model="year">
              <option value="FirstYear">FirstYear</option>
              <option value="SecondYear">SecondYear</option>
              <option value="ThirdYear">ThirdYear</option>
              <option value="FouthYear">FouthYear</option>
            </select>
          </td>
        </tr>
      </table>
      <br />
      <div>
        Information: Name: {{ name }} | Gender: {{ gender }} | Year: {{ year }}
      </div>
    </form>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  name: "App",
  setup() {
    let name = ref("");
    let gender = ref("Female");
    let year = ref("");

    return {
      name,
      gender,
      year,
    };
  },
};
</script>

