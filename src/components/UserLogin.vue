<template>
  <div class="container">
    <div class="left-box">
      <div class="header">
        <h1>Register</h1>
      </div>
      <div class="form-group">
        <label>First Name:</label>
        <input type="text" class="controls" placeholder="Enter First Name" v-model="firstName">
      </div>
      <div class="form-group">
        <label>Last Name:</label>
        <input type="text" class="controls" placeholder="Enter Last Name" v-model="lastName">
      </div>
      <div class="form-group">
        <label>Gender:</label>
        <select class="controls" v-model="gender">
          <option :value="null" selected>Select Gender</option>
          <option value="Female">Female</option>
          <option value="Male">Male</option>
          <option value="Other">Other</option>
        </select>
      </div>
      <div class="form-group">
        <label>Age:</label>
        <input type="number" class="controls" placeholder="Enter Age" v-model="myAge">
      </div>
      <div class="form-group">
        <label>Score:</label>
        <input :type="number" class="controls" placeholder="Enter Score" v-model="myScore">
      </div>
    </div>
    <div class="right-box">
      <div class="content">
        <h2>Display form</h2>
        <img src="../assets/pnc.png" alt="pnc">
      </div>
      <ul>
        <li class="info">First name: {{ firstName }}</li>
        <li class="info">Last name: {{ lastName }}</li>
        <li class="info">Full name: {{ fullName }}</li>
        <li class="info">Gender: <strong :style="{ color: genderColor }">{{ gender }}</strong></li>
        <li class="info">Age: <strong :style="{ color: ageCategory.color }">{{ ageCategory.ageLevel }}</strong></li>
        <li class="info">Score: <strong :style="{ color: scoreInfo.color }">{{ scoreInfo.scoreLevel }}</strong></li>

      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      firstName: "",
      lastName: "",
      gender: null,
      myAge: "",
      myScore: "",
    };
  },

  computed: {
    fullName() {
      return this.firstName + ' ' + this.lastName;
    },

    genderColor() {
      const colors = {

        Male: 'blue',
        Female: 'pink',
        Other: 'green'
      };
      return colors[this.gender] || 'black'; 
    },

    ageCategory() {
      const age = parseInt(this.myAge);
      let ageLevel = "";
      let color = "";

      if (isNaN(age)) {
        ageLevel = " ";
        color = " ";
      } else if (age >= 1 && age <= 13) {
        ageLevel = "Child";
        color = "blue"; 
      } else if (age >= 14 && age <= 18) {
        ageLevel = "Young";
        color = "orange"; 
      } else if (age >= 19 && age <= 30) {
        ageLevel = "Adult";
        color = "green"; 
      } else if (age > 30) {
        ageLevel = "Old";
        color = "gray"; 
      } else if (age === 0) {
        ageLevel = "My age is unknown.";
        color = "black"; 
      }

      return { ageLevel, color };
    },

    scoreInfo() {
      const score = parseInt(this.myScore);
      let scoreLevel = "";
      let color = "";

      if (isNaN(score) || score < 0) {
        scoreLevel = " ";
        color = "black";
      } else if (score >= 0 && score <= 50) {
        scoreLevel = "F";
        color = "red";
      } else if (score > 50 && score <= 60) {
        scoreLevel = "E";
        color = "#FF4500"; 
      } else if (score > 60 && score <= 70) {
        scoreLevel = "D";
        color = "#FFA500"; 
      } else if (score > 70 && score <= 80) {
        scoreLevel = "C";
        color = "yellow";
      } else if (score > 80 && score <= 90) {
        scoreLevel = "B";
        color = "#ADFF2F"; 
      } else if (score > 90 && score <= 100) {
        scoreLevel = "A";
        color = "green";
      } else {
        scoreLevel = "The score is not between 1 to 100";
        color = "black";
      }

      return { scoreLevel, color };
    }

  }
}; 

</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  display: flex;
  justify-content: center;
}

.header h1 {
  color: aliceblue;
}

.form-group input::placeholder {
  color: rgb(167, 241, 242);
}
.form-group label {
  color: rgb(235, 250, 176);
  font-weight: bold;
}
input, select{
  outline: none;
  border-radius: 5px;
  border: 1.5px solid rgb(255, 255, 255);
  color: rgb(235, 250, 176);
  background-color: transparent;
  
}

select {
  content: "Select Gender";
  position: relative;
 
}


option[value], option:nth-child(1) {
  color: rgb(14, 86, 153);
  background: transparent;
} 


.left-box {
  background-image: url(../assets/flower.jpg);
  background-repeat: no-repeat ;
  background-size: cover;
  border: 2px solid orange;
  padding: 10px 25px;
  border-right: none;
  border-radius: 10px 0px 0px 10px;
}

.right-box {
  border: 2px solid teal;
  padding: 10px 25px;
  width: 30%;
  border-left: none;
  border-radius: 0px 10px 10px 0px;
  background: #dae1e05a;
}
.right-box .content img {
  width: 100px;
  height: 100px;
  border-radius: 100%;
  margin: 10px 0px 25px 20px;
}

.content {
  display: flex;
  justify-content: space-between;
}
.content h2 {
  text-transform: uppercase;
  display: flex;
  align-items: end;
  margin: 20px 0px;
}

.form-group {
  margin-bottom: 10px;
  display: flex;
  flex-direction: column;
  text-align: left;
}

label {
  padding-bottom: 10px;
}

.controls {
  padding: 10px;
  width: 500px;
  box-sizing: border-box;
}

ul {
  list-style: none;
  margin: 0;
  padding: 0;
  text-align: left;
}

ul .info {
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 5px ;
}
</style>
