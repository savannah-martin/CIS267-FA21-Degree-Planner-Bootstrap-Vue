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
              :href="'#' + course.id.split(' ').join('')"
              class="card-link fw-light"
              v-b-toggle="course.id.split(' ').join('')"
              >Course description ›</a
            >
          </div>
        </div>

        <b-collapse
          class="course-description collapse card-text"
          :id="course.id.split(' ').join('')"
        >
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
  data() {
    return {
      options: [
        { value: null, text: "Please select an option" },
        { value: "fall2020", text: "Fall 2020" },
        { value: "spring2021", text: "Spring 2021" },
        { value: "fall2021", text: "Fall 2021" },
        { value: "spring2022", text: "Spring 2022" },
        { value: "fall2022", text: "Fall 2022" },
        { value: "spring2023", text: "Spring 2023" },
        { value: "fall2024", text: "Fall 2024" },
        { value: "spring2024", text: "Spring 2024" },
      ],
      selected: null,
    };
  },
  methods: {
    add() {
      this.$emit("add-course", this.course.id);
    },
    methods: {
      convertID(courseID) {
        return courseID.string.split(" ").join("").toLowerCase();
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
      href() {
        var id = this.course.id
          .replace(" ", "")
          .replace("/", "-")
          .toLowerCase();
        return "#" + id;
      },
      shortID() {
        return this.course.id.split(" ").join("");
      },
    },
  },
};
</script>

<style></style>
