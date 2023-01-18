<template>
  <resume-section title="QUALIFICATIONS">
    <div class="section libs">
      <h2>frameworks</h2>
      <div class="section tags">
        <p v-for="lib in frameworks" :key="lib">{{ lib }}</p>
      </div>
    </div>
    <div class="section langs">
      <h2>front-end</h2>
      <div class="tags">
        <p v-for="lang in languages" :key="lang">{{ lang }}</p>
      </div>
    </div>
    <div class="section middleware">
      <h2>middleware</h2>
      <div class="section tags">
        <p v-for="lib in middleware" :key="lib">{{ lib }}</p>
      </div>
    </div>
    <div class="section testings">
      <h2>testing</h2>
      <div class="section tags">
        <p v-for="tdd in testings" :key="tdd">{{ tdd }}</p>
      </div>
    </div>
    <div class="section databases">
      <h2>database</h2>
      <div class="section tags">
        <p v-for="database in databases" :key="database">{{ database }}</p>
      </div>
    </div>
    <div class="section techs">
      <h2>devop technologies</h2>
      <div class="tags">
        <p v-for="tech in technologies" :key="tech">{{ tech }}</p>
      </div>
    </div>
    <div class="section clouds">
      <h2>cloud</h2>
      <div class="tags">
        <p v-for="cloud in clouds" :key="cloud">{{ cloud }}</p>
      </div>
    </div>
    <div class="section scriptings">
      <h2>scripting</h2>
      <div class="section tags">
        <p v-for="script in scriptings" :key="script">{{ script }}</p>
      </div>
    </div>
    <div class="section uidesigns">
      <h2>ui design</h2>
      <div class="section tags">
        <p v-for="lib in uidesigns" :key="lib">{{ lib }}</p>
      </div>
    </div>
  </resume-section>
</template>

<script>
import Section from './Section.vue'

// The default prop "type".
const propType = { type: Array, default: () => [] }

export default {
  props: {
    languages: propType,
    frameworks: propType,
    technologies: propType,
    clouds: propType,
    middleware: propType,
    testings: propType,
    scriptings: propType,
    databases: propType,
    uidesigns: propType,
  },
  components: { 'resume-section': Section },
}
</script>

<style lang="scss" scoped>
@import '@/mixins/_colors.scss';

// prettier-ignore
.section { margin-bottom: .5em; }

h2 {
  margin-bottom: 0.15em;
  font-size: 11.25pt;
  color: #606060;
}

.tags {
  display: flex;
  flex-wrap: wrap;

  p {
    margin: 0 0.25em 0.25em 0;
    padding: 0.16em 0.4em;
    border-radius: 0.25em;
    font-size: 11.25pt;
  }
}

.langs p {
  background-color: rgba($lang-color, 0.22);
  color: $lang-color-dark;
}

.libs p {
  background-color: rgba($lib-color, 0.22);
  color: $lib-color-dark;
}

.uidesigns p {
  background-color: rgba($uidesign-color, 0.22);
  color: $uidesign-color-dark;
}

.middleware p {
  background-color: rgba($middleware-color, 0.22);
  color: $middleware-color-dark;
}

.testings p {
  background-color: rgba($testing-color, 0.22);
  color: $testing-color-dark;
}

.scriptings p {
  background-color: rgba($scripting-color, 0.22);
  color: $scripting-color-dark;
}
.databases p {
  background-color: rgba($database-color, 0.22);
  color: $database-color-dark;
}

.techs p {
  background-color: rgba($tech-color, 0.25);
  color: $tech-color-dark;
}

.clouds p {
  background-color: rgba($cloud-color, 0.22);
  color: $cloud-color-dark;
}
</style>
