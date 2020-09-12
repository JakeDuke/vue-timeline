<template>
  <div class="container">
    <Timeline :points="timelineDataSorted" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator"
import Timeline from "@/components/Timeline.vue"

import rawData from "@/assets/timeline.json"

@Component({
  components: {
    Timeline
  }
})
export default class Home extends Vue {
  get timelineDataSorted() {
    return rawData.sort((a, b) => {
      return new Date(a.registered).getTime() - new Date(b.registered).getTime()
    })
  }
}
</script>
