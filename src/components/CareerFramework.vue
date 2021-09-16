<template>
  <div>
    <table class="matrix-table">
      <caption>
        Dinosaurs in the Jurassic period
      </caption>
      <tbody>
        <tr
          v-for="category in careerFrameworkData"
          :key="category.category"
          :rowspan="category.skills.length"
          class="skills"
        >
          <th :key="category.category" class="category">
            {{ category.category }}
          </th>
          <table class="skill-table">
            <tr v-for="skill in category.skills" :key="skill">
              <th class="skills-description">
                <b>{{ skill.name }}</b>
                <br /><br />
                <em>{{ skill.description }}</em>
              </th>
              <td
                v-for="level in skill.levels"
                :key="level"
                :class="level.level"
                class="level"
              >
                <div v-if="level.criteria.length">
                  <b>{{ level.level }}</b>
                  <br />
                  <ul v-for="criteria in level.criteria" :key="criteria">
                    <li>
                      {{ criteria }}
                    </li>
                  </ul>
                </div>
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

<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}

.matrix-table {
  table-layout: fixed;
  border-collapse: collapse;
  text-align: left;
}

.skill-table {
  padding: 10px;
}

.skills-description {
  padding: 10px;
}

.skills:nth-child(odd) {
  background-color: #e8e8e8;
}
.category {
  padding: 0px 15px;
  transform: rotate(-90deg);
}
.level {
  padding: 10px;
}

.level b {
  text-transform: capitalize;
}
</style>
