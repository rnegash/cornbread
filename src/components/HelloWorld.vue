<template>
  <div class="hello">
    <!-- <h1>{{ skills }}</h1> -->
    <table>
      <thead>
        <tr>
          <td>-</td>
          <th>novice</th>
          <th>beginner</th>
          <th>competent</th>
          <th>proficient</th>
          <th>expert</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="category in careerFrameworkData" :key="category.category">
          <th
            colspan="2"
            :rowspan="category.skills.length"
            :key="category.category"
          >
            {{ category.category }}
          </th>
          <table>
            <tr v-for="skill in category.skills" :key="skill">
              {{
                skill.name
              }}
            </tr>
          </table>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    careerFrameworkData: Array
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

table {
  display: table;
  width: 100%;
}
</style>
