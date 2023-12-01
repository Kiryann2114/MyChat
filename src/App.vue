<script>
import axios from 'axios'

export default {
  data(){
    return{
      ok:"",
      FullName:"",
      Email:"",
      Message:"",
      token: "5999652814:AAHvEOHS6lRCtvf1dnFmMny1zKFeQd1utCE",
      chatId: 691490176
    }
  },
  methods:{
    submit(){
      this.ok = ""
      const FullMessage = `Сообщение от: ${this.FullName}%0AEmail: ${this.Email}%0A%0A${this.Message}`
      axios.post(`https://api.telegram.org/bot${this.token}/sendMessage?chat_id=${this.chatId}&text=${FullMessage}`)
          .then(response => {
            console.log(response);
            this.ok = "СООБЩЕНИЕ УСПЕШНО ОТПРАВЛЕНО"
            },
          error => {
            console.log(error);
            this.ok = "ЧТО-ТО ПОШЛО НЕ ТАК"
          })
    }
  }
}
</script>

<template>
  <form method="POST" @submit.prevent="submit" class="main_cont">
    <div class="cont">
      <lable>Full name</lable>
      <input required v-model="FullName" class="inputs" type="text">
    </div>
    <div class="cont">
      <lable>Email</lable>
      <input required v-model="Email" class="inputs" type="text">
    </div>
    <div class="cont">
      <lable>Massage</lable>
      <textarea required v-model="Message" class="message"></textarea>
    </div>
    <button type="submit" class="button">ОТПРАВИТЬ</button>
    <p class="OK">{{ok}}</p>
  </form>
</template>

<style scoped>
.OK{
  color: #1b6d2e;
  font-size: 17px;
  margin: 0px 10px 10px 10px;
}
.main_cont{
  margin-left: 50%;
  width: 600px;
  background: #282828;
  border-radius: 15px;
}
.cont{
  padding: 10px;
  display: flex;
  flex-direction: column;
  font-size: 25px;
  color: #8e8d89;
}
.inputs{
  font-size: 20px;
  background: #181818;
  border-radius: 10px;
  border-width: 0px;
  height: 40px;
  color: #8e8d89;
}
.message{
  font-size: 20px;
  height: 150px;
  background: #181818;
  border-radius: 10px;
  border-width: 0px;
  color: #8e8d89;
}
.button{
  font-size: 35px;
  background: #2c3e50;
  text-align: center;
  margin: 10px 10px 20px 10px;
  border-radius: 10px;
  border-width: 0px;
  color: #8e8d89;
  height: 60px;
  width: 580px;
}
.button:hover{
  background: #475a6d;
}
</style>