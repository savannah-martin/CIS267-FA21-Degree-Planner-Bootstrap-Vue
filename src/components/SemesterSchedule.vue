<template>
  <div>
    <div class="accordion-item">
      <h2
        class="accordion-header"
        id="fall2019heading"
        v-b-toggle:[schedule.collapseId]
      >
        <div class="">
          <h4 class="my-0">{{ schedule.name }}</h4>
        </div>
      </h2>
      <b-collapse :id="schedule.collapseId">
        <div class="accordion-body">
          <table class="table table-hover">
            <thead>
              <th>Course</th>
              <td></td>
              <td></td>
              <th>Credits</th>
            </thead>
            <tr v-for="c in schedule.classes" :key="c.id">
              <td>{{ c.id }}</td>
              <td>
                <span class="fw-bold">{{ c.name }} </span>
              </td>
              <td>
                <span class="badge bg-primary">
                  {{ c.category }}
                </span>
              </td>
              <td>{{ c.hours }}</td>
            </tr>
            <tr>
              <td></td>
              <td></td>
              <td></td>
              <td class="fw-bold">14</td>
            </tr>
          </table>
        </div>
      </b-collapse>
    </div>
  </div>
</template>

<script>
export default {
  name: "SemesterSchedule",
  props: { schedule: Object},
  methods: {
    remove(id) {
      this.$emit("remove-course", id);
    },
  },
};
</script>

<style></style>
