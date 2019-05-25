<template>
  <div class="wrapper-content wrapper-content--fixed">
    <section>
      <div class="container">
        <table>
          <thead>
            <tr>
              <th>Name</th>
              <th>Age</th>
              <th>Gender</th>
            </tr>
          </thead>

          <tbody>
            <tr v-for='user in users' :key="user.id">
              <td>
                <img :src="user.img" :alt="user.name">
                <span> {{ user.name }} </span>
              </td>
              <td> {{ user.age }} </td>
              <td> {{ user.gender }} </td>
            </tr>
          </tbody>
        </table>
      </div>
    </section>
  </div>
</template>

<script>

import axios from 'axios'
export default {
  data () {
    return {
      users: []
    }
  },
  created () {
    axios
      .get('https://api.myjson.com/bins/rzgya')
      .then(response => {
        this.users = response.data
      })
      .catch(error => {
        console.log(error)
      })
    // this.users = [
    //   { id: 1, name: 'Jach', age: 22, gender: 'male' },
    //   { id: 1, name: 'Alex', age: 24, gender: 'male' }
    // ]
  }
}
</script>

<style lang="scss" scoped>
img {
  width: 60px;
  height: auto;
  border-radius: 50%;
  margin-right: 16px;
}
</style>
