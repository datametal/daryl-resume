<template>
  <resume-section title="RECENT PROJECTS">
    <div class="item" v-for="(proj, i) in data" :key="i">
      <a v-if="proj.name" class="link" :href="proj.name.url" target="_blank">
        <h3 class="name">{{ proj.name.title }}</h3>
      </a>
      <div class="description">
        <a v-if="proj.link" class="link" :href="proj.link.url" target="_blank">
          <h4>{{ proj.link.title }}</h4>
        </a>
        <h4 v-if="proj.timestamp" class="timestamp">{{ proj.timestamp }}</h4>
        <a
          v-if="proj.flair && proj.flair.url"
          class="flair"
          :href="proj.flair.url"
          target="_blank"
        >
          <h5>{{ proj.flair.title }}</h5>
        </a>
        <h5 v-else-if="proj.flair" class="flair">{{ proj.flair }}</h5>
      </div>
      <ul class="points">
        <li v-for="(point, j) in points[i]" :key="j" v-html="point" />
      </ul>
    </div>
  </resume-section>
</template>

<script>
import Section from './Section.vue'
import emphParse from '@/utils/emphParse.js'

export default {
  props: {
    data: { type: Array, default: () => [] },
  },
  computed: {
    points: function() {
      return this.data.map(({ points }) => points.map(emphParse))
    },
  },
  components: { 'resume-section': Section },
}
</script>

<style lang="scss" scoped>
.name {
  font-weight: 600;
  font-size: 12.25pt;
  margin-bottom: 0.15em;
}

.description {
  display: flex;
  align-items: center;
}

// prettier-ignore
.link h4, .timestamp {
  font-weight: 500;
  font-size: 10.5pt;
  margin-right: .7em;
}

// prettier-ignore
.link { text-decoration: none; }

// prettier-ignore
h5.flair, a.flair h5 {
  padding: 0.2em 0.4em;
  border-radius: 0.25em;
  background-color: #f1f1f1;

  font-size: 9.5pt;
  font-weight: 500;
  color: grey;
}

// prettier-ignore
a.flair { text-decoration: none; }

.points {
  margin: 0.2em 0 1em 0;
  padding-left: 1.5em;

  color: #4d4d4d;
  font-size: 11.25pt;

  li {
    margin-top: 0.3em;
    margin-bottom: 0.4em;
    list-style-type: none;

    /deep/ p {
      display: inline;

      // prettier-ignore
      span.emphasis { color: rgb(0, 0, 0); }
    }

    &::before {
      margin-left: -2em;
    }
  }
}
</style>
