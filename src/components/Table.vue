<template>
 <div id="wrap" class="input">
 
  <section class="input-content">
    <h2>Avto Park<span>Test rejim</span></h2>
    <div class="input-content-wrap">
      <dl class="inputbox">
        <dt class="inputbox-title">Avtomobil egasi</dt>
        <dd class="inputbox-content">
          <input id="input0" type="text" required v-model="avto.name"/>
          <label for="input0">Ism</label>
          <span class="underline"></span>
        </dd>
      </dl>
      <dl class="inputbox">
        <dt class="inputbox-title">Avtomobil kirish vaqti</dt>
        <dd class="inputbox-content">
          <input id="input1" type="time" required v-model="avto.time"/>
          <label for="input1">kirish vaqti</label>
          <span class="underline"></span>
        </dd>
      </dl>
      <dl class="inputbox">
        <dt class="inputbox-title">Avtomobil turi</dt>
        <dd class="inputbox-content">
          <select name="" id="" v-model="avto.tur">
                <option  v-for="avtotype of avtoTur" :value="avtotype">
                {{ avtotype }}
            </option>
          </select>
         
         
        </dd>
      </dl>
      <dl class="inputbox">
        <dt class="inputbox-title">Moshina brendi</dt>
        <dd class="inputbox-content">
            
            <input id="input2" type="text" required v-model="avto.brend"/>
          <label for="input2">Moshina brendi</label>
          <span class="underline"></span>
         
        </dd>
      </dl>

      <div class="btns">
        <button class="btn btn-confirm" @click="add">Qo'shish</button>
      </div>

      <div class="table-statistik">
        <div v-if="son">
            <h1>Joylar soni {{ joysoni }} ta 😊</h1>
        </div>
        <div v-else>
            <h1>Joylar qolmadi 😉 </h1>
        </div>
        <h1>Bo'sh joylar {{ joysoni - this.avtoSucces.length }} ta</h1>
        <h1>Bugunlik tushum {{ this.avtoSucces.length * summa }}</h1>
    </div>
     
    </div>
  </section>
</div>
    
<div class="table-bar">
    <div class="box-wrap">
        <div class="table-wrap">
            <table v-if="avtoSucces.length>0">
                <thead>
                    <tr>
                        <th>T/R</th>
                        <th>Ism</th>
                        <th>Vaqt</th>
                        <th>Moshina turi</th>
                        <th>Brend</th>
                    </tr>
                </thead>
                <tbody>
               <tr v-for="person,index  of avtoSucces">
                <td>{{ index + 1 }}</td>
                <td>{{ person.name }}</td>
                <td>{{ person.time }}</td>
                <td>{{ person.tur }}</td>
                <td>{{ person.brend }}</td>
               </tr>
                </tbody>
            </table>
        </div>

      
    </div>
</div>
</template>

<script>
export default {
    data() {
        return {
            avto: {},
            avtoTur : ['Yuk moshina', 'Yengil moshina'],
            avtoSucces : [],
            joysoni: 20,
            son:true,
            summa: 5000,
        }
    },

    methods: {
        add() {
          
            if(this.avtoSucces.length === 20 ) {
               this.son = false
            }else {
                this.avtoSucces.push(this.avto)
                this.avto = {}
            }
        }
    }

}
</script>

<style>



#wrap {
  width: 100%;
  max-width: 900px;
  margin: 0 auto 60px;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.25);
}

.input::before {
  content: "";
  display: block;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 300px;
  background: #0f1041;
}


.input-content {
  position: relative;
  padding: 44px 55px;
  background: #fff;
  z-index: 10;
}
.input-content h2 {
  padding-bottom: 45px;
  font-size: 1.625em;
  font-weight: bold;
  vertical-align: middle;
}
.input-content h2 span {
  display: inline-block;
  margin-left: 10px;
  padding: 5px 6px 3px;
  border: 1px solid #ffca00;
  border-radius: 4px;
  font-size: 0.85rem;
  vertical-align: middle;
  color: #ffca00;
}
.input-content .inputbox {
  overflow: hidden;
  position: relative;
  padding: 15px 0 28px 200px;
}
.input-content .inputbox-title {
  position: absolute;
  top: 15px;
  left: 0;
  width: 200px;
  height: 30px;
  color: #666;
  font-weight: bold;
  line-height: 30px;
}
.input-content .inputbox-content {
  position: relative;
  width: 100%;
}
.input-content .inputbox-content input {
  width: 100%;
  height: 30px;
  box-sizing: border-box;
  line-height: 30px;
  font-size: 14px;
  border: 0;
  background: none;
  border-bottom: 1px solid #ccc;
  outline: none;
  border-radius: 0;
  -webkit-appearance: none;
}
.input-content .inputbox-content input:focus ~ label, .input-content .inputbox-content input:valid ~ label {
  color: #2962ff;
  transform: translateY(-20px);
  font-size: 0.825em;
  cursor: default;
}
.input-content .inputbox-content input:focus ~ .underline {
  width: 100%;
}
.input-content .inputbox-content label {
  position: absolute;
  top: 0;
  left: 0;
  height: 30px;
  line-height: 30px;
  color: #ccc;
  cursor: text;
  transition: all 200ms ease-out;
  z-index: 10;
}
.input-content .inputbox-content .underline {
  content: "";
  display: block;
  position: absolute;
  bottom: -1px;
  left: 0;
  width: 0;
  height: 2px;
  background: #2962ff;
  transition: all 200ms ease-out;
}
.input-content .btns {
  padding: 30px 0 0 200px;
}
.input-content .btns .btn {
  display: inline-block;
  margin-right: 2px;
  padding: 10px 25px;
  background: none;
  border: 1px solid #c0c0c0;
  border-radius: 2px;
  color: #666;
  font-size: 1.125em;
  outline: none;
  transition: all 100ms ease-out;
}
.input-content .btns .btn:hover, .input-content .btns .btn:focus {
  transform: translateY(-3px);
}
.input-content .btns .btn-confirm {
  border: 1px solid #2962ff;
  background: #2962ff;
  color: #fff;
}
.table-statistik {
    padding: 20px;
}
.table-statistik h1{
    line-height: 50px;
}
.table-wrap {
  max-width: 800px;
  margin: 80px auto;
  overflow-x: auto;
}

table, td, th {
  border: 1px solid #ddd;
  text-align: left;
}

table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  padding: 15px;
  white-space: nowrap;
}

table tbody tr:nth-child(odd) {
  background: rgb(226, 226, 226);
}

.box-wrap {
  padding: 0px 16px;
}
</style>