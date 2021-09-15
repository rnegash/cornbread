<template>
  <div>
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
                ><br /><br />
                <em>{{ skill.description }}</em>
              </td>
              <td v-for="level in skill.levels" :key="level" class="level">
                <b>{{ level.level }}</b
                ><br />
                <ul v-for="criteria in level.criteria" :key="criteria">
                  <li>
                    {{ criteria }}
                  </li>
                </ul>
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
  name: "CareerFramework",
  props: {
    careerFrameworkData: Array
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}

table {
  display: table;
  width: 100%;
  text-align: left;
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
.level {
  padding: 10px;
}

.level b {
  text-transform: capitalize;
}
</style>
