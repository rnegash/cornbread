<template>
  <div>
    
    <LevelChooser identifier="primary" @role-change="roleChanged" />
    <LevelChooser identifier="secondary" @role-change="roleChanged" />

    <table aria-label="The entire skill matrix in table form" class="matrix-table">
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
          <table aria-label="Tabulation of the requirements for a particular skill" class="skill-table">
            <tr v-for="skill in category.skills" :key="skill" >
              <th scope="row" class="skills-description" >
                <strong>{{ skill.name }}</strong>
                <br /><br />
                <em>{{ skill.description }}</em>
              </th>
              <td
                v-for="level in skill.levels"
                :key="level"
                :class="[level.level, skill.id]"
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
  import LevelChooser from "./LevelChooser.vue";
  export default {
    name: "CareerFramework",
    components: {
      LevelChooser
    },
    props: {
        careerFrameworkData: Array,
        roleData: Array
    },
    methods:{

      roleChanged(eventObject){

        let role = eventObject.roleValue;
        let isHighlightedSelector = '';

        if(eventObject.controlIdentifier === 'primary') {
          isHighlightedSelector = 'highlighted'
        }else {
          isHighlightedSelector = 'second-highlight'
        }

        console.log('whoah: ' + role);

        let highlightedElements = document.querySelectorAll('.' + isHighlightedSelector);
        highlightedElements.forEach(e => e.classList.remove(isHighlightedSelector));


        let filteredData = this.roleData.filter(function (e) {
          return e.role===role;
        });
        
        let levelDetails = filteredData[0].expectations.map(a => a.levels);
        levelDetails.forEach(function doTheThing(element){          
          Object.keys(element).forEach(function(key) {
            if(element[key] !== 'N/A') {
              let selector = '.' + key + '.' + element[key];
              console.log(selector.toLowerCase());
              let elements = document.querySelectorAll(selector.toLowerCase());
              elements.forEach(e => e.classList.add(isHighlightedSelector));
            }
          });
        });
        
        //Apply highlighted class to each of the above
      }
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
  width: 250px;
  padding: 10px;
  vertical-align: top;
}

.skills:nth-child(odd) {
  background-color: #e8e8e8;
}

.category {
  padding: 0px 15px;
  white-space: nowrap;
  max-width: 1em;
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

.highlighted {
  background-color: rgba(127, 255, 212, 0.5);
}

.second-highlight {
  background-color: rgba(127, 193, 255, 0.5);
}

.highlighted.second-highlight {
  background-color: rgba(127,227,232, 0.5);
}
</style>
