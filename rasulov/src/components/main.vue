<template>
  <div>
      <div class="container rounded border border-secondary mt-5">
            <h1 class="h1 text-center text-info w-100 bg-light">
                IT Отдел в Норвегии города Осло
            </h1>
            <div class="row">
                <div class="col-4"><img src="media/item1.jpg" alt="" class="img-fluid m-2"></div>
                <div class="col-4"><img src="media/item2.jpg" alt="" class="img-fluid m-2"></div>
                <div class="col-4"><img src="media/item3.jpg" alt="" class="img-fluid m-2"></div>
            </div>
            <div class="row">
                <div class="col-4"><img src="media/item4.jpg" alt="" class="img-fluid m-2"></div>
                <div class="col-4"><img src="media/item5.jpg" alt="" class="img-fluid m-2"></div>
                <div class="col-4"><img src="media/item6.jpg" alt="" class="img-fluid m-2"></div>
            </div>
            <picture class="image text-center">
                <source class="source" media="(max-width: 1100px)" srcset="media/imgOne.png">
                <img srcset="media/imgOne.png 378w,
                            media/211.png"
                        sizes="(max-width: 830px) 378px"
                        src="media/211.png" alt="Elva dressed as a fairy">
            </picture>
      </div>
  </div>
</template>