<template>
  <div id="app">
    <div v-for="(rank, i) in list" :key="i" class="row">
      <div class="col-3">
        <p>{{ rank.name }}</p>
      </div>
      <div class="col-2">
        <button @click="updateRank(rank)">Update</button>
      </div>
      <div class="col-2">
        <button @click="deleteRank(rank.id)">Delete</button>
      </div>
    </div>
    <button @click="createRank()">Save</button>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      list: []
    };
  },
  methods: {
    updateRank(item) {
      item.name = item.name + "dulal";
      const requestOptions = {
        method: "PUT",
        headers: {
          "Content-Type": "application/json",
          "X-API-KEY": "fgbhdfdhhsbsbsdbsdgsdfbdfbsdbdbd",
          "X-AUTH-TOKEN": "fdgdgdfdfbngnsbhsdbsbhdeky,dhsewhnddddejndfnh",
          "X-DEVICE-ID": "aa="
        },
        body: JSON.stringify(item)
      };
      fetch("http://198.23.221.55:46668/api/ranks", requestOptions)
        .then(response => response.json())
        .then(data => console.log(data));
    },
    createRank() {
      const requestOptions = {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          "X-API-KEY": "fgbhdfdhhsbsbsdbsdgsdfbdfbsdbdbd",
          "X-AUTH-TOKEN": "fdgdgdfdfbngnsbhsdbsbhdeky,dhsewhnddddejndfnh",
          "X-DEVICE-ID": "aa="
        },
        body: JSON.stringify({ name: "ABC", type: "STUFF" })
      };
      fetch("http://198.23.221.55:46668/api/ranks", requestOptions)
        .then(response => response.json())
        .then(data => console.log(data));
    },
    deleteRank(id) {
      const requestOptions = {
        method: "DELETE",
        headers: {
          "Content-Type": "application/json",
          "X-API-KEY": "fgbhdfdhhsbsbsdbsdgsdfbdfbsdbdbd",
          "X-AUTH-TOKEN": "fdgdgdfdfbngnsbhsdbsbhdeky,dhsewhnddddejndfnh",
          "X-DEVICE-ID": "aa="
        }
      };
      fetch(
        "http://198.23.221.55:46668/api/ranks?type=STUFF&id=" + id,
        requestOptions
      )
        .then(response => response.json())
        .then(data => console.log(data));
    }
  },
  mounted() {
    const headers = {
      "Content-Type": "application/json",
      "X-API-KEY": "fgbhdfdhhsbsbsdbsdgsdfbdfbsdbdbd",
      "X-AUTH-TOKEN": "fdgdgdfdfbngnsbhsdbsbhdeky,dhsewhnddddejndfnh",
      "X-DEVICE-ID": "aa="
    };
    fetch("http://198.23.221.55:46668/api/ranks?type=STUFF&size=120", {
      headers
    })
      .then(response => response.json())
      .then(data => {
        this.list = data.list;
      });
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
