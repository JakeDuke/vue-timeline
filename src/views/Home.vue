<template>
  <div class="home">
    <Timeline :points="timelineData" />
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
  get timelineData () {
    return rawData
  }
}
</script>
