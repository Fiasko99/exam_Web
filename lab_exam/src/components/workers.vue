<template>
  <div>
    <div class="container">
        <h1 class="h1 text-center w-100 text-primary">Работники отделов</h1>
        <div class="row border border-info text-center mb-2 p-1 rounded-lg" v-for="worker in workers" :key="worker.id" @click="onRedact(worker.id)">
            <div class="col-sm-3">{{ worker['surname'] }}</div>
            <div class="col-sm-3">{{ worker['name'] }}</div>
            <div class="col-sm-3">{{ worker['patronymic'] }}</div>
            <div class="col-sm-3">{{ dapartaments[worker['id_department'] - 1]['value'] }}</div>
        </div>
        <h1 class="h1 text-center w-100 text-primary">Создание сотрудников по отделам</h1>
        <div class="row border rounded border-primery p-1">
            
            <div class="col-lg-4">
                <div class="form-group">
                    <label for="#surnameW">Фамилия</label>
                    <input type="text" id="surnameW" v-model="surname" class="form-control" placeholder="С большой буквы" required>
                </div>
            </div>
            <div class="col-lg-4">
                <div class="form-group">
                    <label for="#nameW">Имя</label>
                    <input type="text" id="nameW" v-model="name" class="form-control" placeholder="С большой буквы" required>
                </div>
            </div>
            <div class="col-lg-4">
                <div class="form-group">
                    <label for="#patronymicW">Отчество</label>
                    <input type="text" id="patronymicW" v-model="patronymic" class="form-control" placeholder="С большой буквы" required>
                </div>
            </div>

        </div>
        <div class="row mb-2">
            <div class="col-12">
                <select id="myRole" class="form-group m-2 w-100" v-model="id_department">
                    <option value="0" disabled selected="selected">Выбрать отдел</option>
                    <option value="1">Юридический отдел</option>
                    <option value="2">Отдел продаж</option>
                    <option value="3">Доставки отдел</option>
                    <option value="4">IT отдел</option>
                </select>
            </div>
        </div>
        <div class="row">
            <div class="col-md-4 w-100 text-center mb-3"><button class="btn btn-outline-dark" @click="onSend()">Сохранить</button></div>
            <div class="col-md-4 w-100 text-center mb-3"><button class="btn btn-outline-dark" @click="onTurnRedact()" ref="redactBTN">Изменить</button></div>
            <div class="col-md-4 w-100 text-center"><button class="btn btn-outline-dark" @click="updateData()">Показать список</button></div>
        </div>
    </div>
  </div>
</template>

            
<script>
  export default {
    name: 'App',
    data() {
      return {
        workers: [],
        dapartaments: [],
        surname: '',
        name: '',
        patronymic: '',
        id_department: 0,
        redact: false,
      };
    },
    components: {},
    methods: {
        async updateData() {
            try {
                await this.$http
                    .get('http://localhost:5000/workers')
                    .then((res) => res.json())
                    .then((res) => (this.workers = res));
            } catch (err) {
                console.error(err);
            }
            try {
                await this.$http
                    .get('http://localhost:5000/departments')
                    .then((res) => res.json())
                    .then((res) => (this.dapartaments = res));
            } catch (err) {
                console.error(err);
            }
        },

        async onSend() {
            if (this.id_department != 0) {
                let worker = {
                    "surname": this.surname,
                    "name": this.name,
                    "patronymic": this.patronymic,
                    "id_department": Number(this.id_department)
                }
                try {
                    await this.$http.post('http://localhost:5000/workers', worker);
                    this.updateData();
                    alert('Сотрудник сохранен')
                } catch (err) {
                    console.error(err);
                }
            } else {
                alert("Выберите отдел сотрудника")
            }
        },

        onTurnRedact() {
            this.redact = !this.redact;
            this.$refs.redactBTN.innerHTML = this.redact ? "Изменение" : "Изменить";
        },

        async onRedact(id_worker) {
            if (this.redact) {
                let worker = {
                    "surname": this.surname,
                    "name": this.name,
                    "patronymic": this.patronymic,
                    "id_department": Number(this.id_department)
                }
                await this.$http.put(`http://localhost:5000/workers/${id_worker}`, worker)
                this.updateData();
            }
        },

        created() {
            this.updateData();
        },
  }
}
</script>

    

