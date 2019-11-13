<template>
  <div class="resume">
    <resume-header v-bind="headerData" />
    <div class="content">
      <skills v-bind="skillsData" />
      <projects :data="projectsData" />
      <experience :data="experienceData" />
      <education :data="educationData" />
      <!-- <div class="column left">
        <experience :data="experienceData" />
      </div>
      <div class="column right">
        <skills v-bind="skillsData" />
        <projects :data="projectsData" />
        <education :data="educationData" />
      </div>-->
    </div>
    <badge :source="badgeData" />
  </div>
</template>

<script>
import _ from 'lodash'
import Header from '@/components/Header.vue'
import Experience from '@/components/Experience.vue'
import Skills from '@/components/Skills.vue'
import Projects from '@/components/Projects.vue'
import Education from '@/components/Education.vue'
import Badge from '@/components/Badge.vue'

export default {
  props: {
    data: { type: Object, required: true },
  },
  computed: {
    headerData: function() {
      return _.pick(this.data, ['name', 'blurb', 'links']) || {}
    },
    experienceData: function() {
      return this.data.experiences
    },
    skillsData: function() {
      return this.data.skills
    },
    projectsData: function() {
      return this.data.projects
    },
    educationData: function() {
      return this.data.education
    },
    badgeData: function() {
      const { meta } = this.data
      return meta ? meta.source : undefined
    },
  },
  components: {
    'resume-header': Header,
    Experience,
    Skills,
    Projects,
    Education,
    Badge,
  },
}
</script>

<style lang="scss" scoped>
.resume {
  width: 8.5in;
  height: 55in;
  display: flex;
  flex-direction: column;

  background-color: white;
}
.section {
  width: 95%;
  display: -moz-box;
  -moz-box-orient: vertical;
  -webkit-box-orient: vertical;
  -webkit-flex-direction: row;
  -ms-flex-direction: row;
  flex-direction: row;
  padding: 2em;
  padding-top: 1.2em;
  padding-right: 0.8em;
  flex: 1;
}
.content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 90%;
  max-width: 90%;
  margin: 0 auto;
  padding-left: 15px;
  padding-right: 15px;
}

// prettier-ignore
.footer-badge { margin: 0 auto 3em auto; }
</style>
