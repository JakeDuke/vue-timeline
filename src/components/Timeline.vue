<template>
  <div class="main">
    <div class="timeline">
      <div v-for="(point, idx) in points" :key="idx">
        <!-- EMPTY HEIGHT-->
        <div class="cd-timeline-block">
          <div class="cd-timeline-card-pure" />
          <div class="cd-timeline-progress">
            <div class="cd-timeline-bar" />
            <div class="cd-timeline-bar" />
            <div class="cd-timeline-bar" />
          </div>
          <div class="cd-timeline-card-pure" />
        </div>
        <!-- RIGHT BOX-->
        <div v-if="idx % 2 === 1" class="cd-timeline-block">
          <div class="cd-timeline-card-pure"></div>
          <div class="cd-timeline-progress">
            <div class="cd-timeline-bar" />
            <div class="cd-timeline-point" />
            <div class="cd-timeline-bar" />
          </div>
          <div class="cd-timeline-card">
            <div class="p-timeline-box current">
              <h3 class="text-center">
                {{ point.name.first }} {{ point.name.last }}
              </h3>
              <div class="cd-timeline-card-content">
                <p>{{ point.about }}</p>
              </div>
              <div class="mb-2">
                <b>Tags: </b>
                <span>{{ formatTags(point.tags) }}</span>
              </div>
              <em>
                <b>{{ point.registered }}</b>
              </em>
            </div>
          </div>
        </div>
        <!-- LEFT BOX-->
        <div v-else class="cd-timeline-block">
          <div class="cd-timeline-card">
            <div class="p-timeline-box current">
              <h3 class="text-center">
                {{ point.name.first }} {{ point.name.last }}
              </h3>
              <div class="cd-timeline-card-content">
                <p>{{ point.about }}</p>
              </div>
              <div class="mb-2">
                <b>Tags: </b>
                <span>{{ formatTags(point.tags) }}</span>
              </div>
              <em>
                <b>{{ point.registered }}</b>
              </em>
            </div>
          </div>
          <div class="cd-timeline-progress">
            <div class="cd-timeline-bar" />
            <div class="cd-timeline-point" />
            <div class="cd-timeline-bar" />
          </div>
          <div class="cd-timeline-card-pure" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { Vue, Component } from "vue-property-decorator"

@Component({
  props: {
    points: {
      type: Array,
      required: true
    }
  }
})
export default class Timeline extends Vue {
  formatTags(tags) {
    return tags.join(", ")
  }
}
</script>

<style lang="scss" scoped>
.main {
  padding: 20px;
  margin-top: 30px;
  font-size: 14px;
}

.about {
  padding-top: 3em;
}

.p-timeline-box {
  padding: 20px;
  border-radius: 2px;
}

.cd-timeline-card {
  text-align: left;
  flex: 3;
  box-sizing: border-box;
  border: 1px solid #c4c4c4;
  border-radius: 15px;
  margin-right: -2px;
}

.cd-timeline-bar {
  flex: 1;
  width: 2px;
  background-color: #c4c4c4;
}

.cd-timeline-point {
  height: 14px;
  width: 14px;
  border-radius: 50%;
  border: 2px solid #c4c4c4;
}

.cd-timeline-block {
  position: relative;
  width: 90%;
  display: flex;
  flex-direction: row;
  align-items: stretch;
  margin: 0 auto;
}

.cd-timeline-card-pure {
  box-sizing: border-box;
  border: none;
  flex: 3;
  text-align: right;
  align-items: center;
  display: flex;
  justify-content: flex-end;
}

.cd-timeline-progress {
  display: flex;
  flex-direction: column;
  flex: 1;
  align-items: center;
}
</style>
