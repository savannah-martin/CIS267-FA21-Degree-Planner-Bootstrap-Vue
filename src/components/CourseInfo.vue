<template>
  <div class="my-4 text-left" id="lac-reqs">
    <div class="card my-2">
      <div class="card-body">
        <div class="row">
          <h5 class="col-9">
            <b>{{ course.name }}</b>
          </h5>
          <p class="col-3 text-right">{{ course.hours }} hours</p>
        </div>

        <div class="row">
          <div class="col-8">
            <p class="card-subtitle">{{ course.id }}</p>
          </div>
          <div class="col-4 text-right">
            <span class="text-muted">{{ course.hours }}</span>
          </div>
        </div>
        <div class="row">
          <b-form-select v-model="selected" :options="options"></b-form-select>

          <b-button block @click="add" variant="outline-secondary" class="my-2"
            >Add</b-button
          >
        </div>

        <div class="row">
          <div class="col">
            <a
              href="#bib121"
              class="card-link fw-light"
              v-b-toggle:shortID
              >Course description ›</a
            >
          </div>
        </div>

        <b-collapse class="course-description collapse card-text" :id="shortID">
          <p class="text-muted card-text">
            {{ course.description }}
          </p>
        </b-collapse>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CourseInfo",
  props: { course: Object },
  methods: {
    add() {
      this.$emit("add-course", this.course.id);
    },
    methods: {
      convertID(courseID) {
        return courseID.replace(" ", "").replace("/", "-").toLowerCase();
      },
      makehref() {
        var id = this.course.id
          .replace(" ", "")
          .replace("/", "-")
          .toLowerCase();
        return "#" + id;
      },
    },
    computed: {
      shortID() {
        return this.course.id.replace(" ", "").replace("/", "-").toLowerCase();
      },
    },
  },
};
</script>

<style></style>
