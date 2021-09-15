<template>
  <div class="hello">
    <!-- <h1>{{ skills }}</h1> -->
    <table>
      <caption>
        Dinosaurs in the Jurassic period
      </caption>
      <tbody>
        <tr
          v-for="category in careerFrameworkData"
          :key="category.category"
          class="skills"
        >
          <th
            colspan="2"
            :rowspan="category.skills.length"
            :key="category.category"
            class="category"
          >
            {{ category.category }}
          </th>
          <table>
            <tr v-for="skill in category.skills" :key="skill">
              <td>
                <b>{{ skill.name }}</b
                ><br />
                {{ skill.description }}
              </td>
              <td v-for="level in skill.levels" :key="level">
                <b>{{ level.level }}</b
                ><br />
                {{ level.criteria.join("####") }}
              </td>
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
.skills {
  display: table;
}
.skills:nth-child(odd) {
  background-color: #e8e8e8;
}
.category {
  padding: 15px;
  writing-mode: sideways-lr;
}
</style>
