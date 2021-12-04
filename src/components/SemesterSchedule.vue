<template>
  <div class="box">
    <div class="accordion-item">
      <h2
        class="accordion-header"
        id=""
        v-b-toggle:[schedule.collapseId]
      >
        <div class="d-flex flex-row justify-content-between px-2">
          <div>
            <h4 class="my-0">{{ schedule.name }}</h4>
          </div>
          <div>
            <p class="carat text-right px-4 text-primary">▼</p>
          </div>
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
  props: { schedule: Object },
  methods: {
    remove(id) {
      this.$emit("remove-course", id);
    },
  },
};
</script>

<style>
.box {
  border: 1px solid gray;
  border-radius: 5px;
  padding-top: 14px;
}
.carat {
  font-size: 22px;
}
</style>
