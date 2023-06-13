<template>
  <section class="relative bg-[url(https://img.freepik.com/vector-premium/grupo-personas-cubriendo-sus-rostros-mascaras-que-expresan-emociones-positivas-concepto-ocultar-personalidad-o-individualidad-problema-psicologico-ilustracion-colorida-dibujos-animados-estilo-plano_126608-330.jpg?w=740)] bg-cover bg-center bg-no-repeat">
    <div class="absolute inset-0 bg-white/75 sm:bg-transparent sm:bg-gradient-to-r sm:from-white/95 sm:to-white/25"></div>

    <div class="relative mx-auto max-w-screen-xl px-4 py-32 sm:px-6 lg:flex lg:h-screen lg:items-center lg:px-8">
      <div class="max-w-xl text-center sm:center">
        <h1 class="text-3xl font-extrabold sm:text-5xl">
          ¿Quieres saber que tipo de persona UXD eres?
          <strong class="block font-extrabold text-blue-700">
            
          </strong>
        </h1>
        <div class="mt-8 flex flex-wrap gap-4 text-center">
          <a href="#"
            class="block w-full rounded bg-blue-600 px-12 py-3 text-sm font-medium text-white shadow hover:bg-blue-700 focus:outline-none focus:ring active:bg-blue-500 sm:w-auto">
            <RouterLink to="/about">Registraté!</RouterLink>
          </a>

          <a href="#"
            class="block w-full rounded bg-white px-12 py-3 text-sm font-medium text-blue-600 shadow hover:text-blue-700 focus:outline-none focus:ring active:text-blue-500 sm:w-auto">
            <RouterLink to="//personas">Ver ingresados</RouterLink>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>