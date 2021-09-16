<!-- Account woes-->
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
          <th scope="row" :key="category.category" class="category">
            {{ category.category }}
          </th>
          <table class="skill-table">
            <caption>
              Tabulation of all requirements for a skill
            </caption>
            <tr v-for="skill in category.skills" :key="skill">
              <th scope="row" class="skills-description">
                <strong>{{ skill.name }}</strong>
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
                  <strong>{{ level.level }}</strong>
                  <br />
                  <ul>
                    <li
                      v-for="criteria in level.criteria"
                      :key="criteria"
                      class="criteria"
                    >
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
  vertical-align: top;
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
  vertical-align: top;
}

.level strong {
  text-transform: capitalize;
}

.criteria:not(:last-child) {
  padding-bottom: 10px;
  margin-bottom: 10px;
  border-bottom: 2px black dotted;
}
</style>
