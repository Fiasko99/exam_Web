<template>
  <div id="app">
    <header class="sticky-top">
      <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <router-link class="navbar-brand" to="/main">Rasulov</router-link>
      <img src="media/logo.png" alt="no logo" class="img-sett logo">
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
        <div class="navbar-nav align-right">
          <router-link class="nav-item nav-link" to="/main">Главная</router-link>
          <router-link class="nav-item nav-link" to="/workers">Работники</router-link>
        </div>
      </div>
    </nav>
    </header>
        
    <main>
    <router-view></router-view>
      <div class="container border rounded-sm border-primary mt-5">
        <div class="row m-2">
          <div class="col-lg-6">
            <h5 class="h5 text-center text-wrap w-100 border-bottom border-info text-primary">Для просмотра списка сотрудников, нажмите на "Работники" в шапке.</h5>
          </div>
          <div class="col-lg-6">
            <h5 class="h5 text-center text-wrap w-100 border-bottom border-info text-primary">Для просмотра списка главной страницы, нажмите на "Главная" в шапке.</h5>
          </div>
        </div>
        <div class="row border rounded border-info m-2 bg-custom">
          <h2 class="h2 text-center text-wrap text-white bg-info w-100">Отделы компании</h2>
          <div class="col-md-4 border-right border-dark">
            <label for="imgUrist" class="h6 text-wrap text-center w-100">Юридический отдел</label>
            <img src="media/urist.jpg" alt="no img" class="img-fluid img-thumbnail rounded-lg align-center" id="imgUrist">
          </div>
          <div class="col-md-4 border-right border-dark">
            <label for="imgSales" class="h6 text-wrap text-center w-100">Отдел доставки</label>
            <img src="media/sales.jpg" alt="no img" class="img-fluid img-thumbnail rounded-lg align-center" id="imgSales">
          </div>
          <div class="col-md-4">
            <label for="imgDostavka" class="h6 text-wrap text-center w-100">Отдел продаж</label>
            <img src="media/dostavka.jpg" alt="no img" class="img-fluid img-thumbnail rounded-lg align-center" id="imgDostavka">
          </div>
        </div>
      </div>
    </main>
    <footer class="footer bg-light w-100 mt-5">
        <div class="column-1">
					<h1>Студент</h1>
          <p>Расулов Гасанбег Магомедович</p>
          <p>181-361</p>
          <p>22.06.2020г</p>
				</div>
				
				<div class="column-2">
					<h1>Ссылки</h1>
          <ol>
            <li>
<a href="https://router.vuejs.org/ru/api/#%D1%81%D0%B2%D0%BE%D0%B9%D1%81%D1%82%D0%B2%D0%B0-%D0%BE%D0%B1%D1%8A%D0%B5%D0%BA%D1%82%D0%B0-route" target="_blink">router.vuejs.org</a>
            </li>
            <li>
          <a href="https://router.vuejs.org/ru/api/#%D0%BE%D0%B1%D1%8A%D0%B5%D0%BA%D1%82-route" target="_blink">router.vuejs.org</a>

            </li>
            <li>
          <a href="https://metanit.com/web/vuejs/1.12.php" target="_blink">metanit.com</a>

            </li>
            <li>
          <a href="https://vue-select.org/guide/values.html#transforming-selections" target="_blink">vue-select.org</a>

            </li>
            <li>
          <a href="https://bootstrap-4.ru/docs/4.0/layout/grid/" target="_blink">bootstrap-4.ru</a>

            </li>
          </ol>
				</div>
				
				<div class="column-3">
					<h1>Логотип</h1>
          <img class="img-fluid"
               src="media/logo.png">
				</div>

          
          


          
    </footer>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {}
}
</script>

<style>
* {
  font-family: 'Roboto Mono', monospace;
}
body, html {
  margin: 0;
  padding: 0;
}
body {
  background-color: floralwhite;
}
.img-sett { 
  width: 200px;
}

.bg-custom{
  background-color: lightskyblue;
}
.logo {
  width: 200px;
  animation: pulsing 2s infinite;
}

@keyframes pulsing {
  0% {
    transform: scale(0.5, 0.5)
  }
  50% {
    transform: scale(1.0, 1.0);
  }
  100% {
    transform: scale(0.5, 0.5);
  }
}



@media screen and (min-width: 600px) {
  .footer {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
  }

  .column-1 {
    grid-column-start: 1;
    grid-column-end: 2;
  }

  .column-2 {
    grid-column-start: 2;
    grid-column-end: 3;
  }

  .column-3 {
    grid-column-start: 3;
    grid-column-end: 4;
  }
}
</style>
