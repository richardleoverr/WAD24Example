<template>
  <div>
<h3> All Route  </h3>

<!-- Task 1 -->
    <div class = 'container'>
      <table>    
      <thead>
      <tr>
        <th>From</th>
        <th>To</th>
        <th>Cost</th>
        <th>Time</th>
        <th>Date</th>
      </tr>
          </thead>
          <tbody>
            <tr class = "item" v-for = "route in routes" :key="route.id">
            <td>{{ route.fromcity }}</td>
            <td>{{ route.tocity }}</td>
            <td>{{ route.cost}}</td>
            <td>{{ route.departuretime}}</td>
            <td>{{ route.departuredate }}</td>
          </tr>
          </tbody>
      </table>
    </div>
  </div>
</template>


<script>
export default {
  name: "AllRoutes",
  data() {
    return {
      toTallinn: 0,
      routes: [],

    };
  },
  methods: {
    fetchRouts() {
      fetch(`http://localhost:3000/api/routes/`)
        .then((response) => response.json())
        .then((data) => (this.routes = data))
        .catch((err) => console.log(err.message));
  },
  },
  mounted() {
    this.fetchRouts();
    console.log("mounted");
  } 
};
</script>

<style scoped>



</style>