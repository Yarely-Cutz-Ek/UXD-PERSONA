<script>
import axios from 'axios'

let API_URL = '/api/getPersonasUxd.php'

export default {

    data() {
        return {
            counter: 0,
            //variables de retorno  
            //para lista de personas
            id: 0,
            personas: [],
            infoUno: [],
            mostrar: false,
            buscar:"",
        }
    },
    mounted() {
        axios
            .get(API_URL)
            .then((response) => {
                //paginas
                console.log(response.data.personas);

                this.personas = response.data.personas;

                console.log(this.personas)
            })

    },
    methods: {
        InfoPer(id) {

            //url de consumo API
            API_URL = '/api/getPersonasUxd.php?id=' + id
            console.log(API_URL)
            //lo obtiene
            axios.get(API_URL)
                //
                .then((response) => {
                    console.log(response) //regresa datos de un solo personaje
                    //contiene el array de cada personaje con sus datos
                    this.infoUno = response.data.persona;
                    console.log(this.infoUno)
                })
            //this.id++
            this.mostrar = true
            console.log(this.mostrar)
        },
        buscarpers(){
            
        }
    }
}
</script>

<template class="antialiased bg-gray-100 text-gray-600 h-screen px-4 mb-full">
    <div class="grid grid-cols-4">
        <div>
            <div id="buscar" class="flex">
                <div class="grid grid-cols-2 px-6">
                    <div class="py-2 px-2"><input type="text" name="buscar" id="buscar"
                            class="w-full rounded-lg bg-gray-200 p-3 text-sm text-gray-600" placeholder="buscar"></div>
                    <div class="py-4 px-4"><button
                            class=" rounded-full bg-blue-500 active:bg-blue-600  hover:bg-blue-700 py-1 px-5 text-white ">
                            Buscar</button></div>
                </div>
            </div>
            <div class=" my-auto p-18 py-2">
                <div class="flex flex-col justify-center ">
                    <!-- Table -->
                    <div class="flex flex-wrap">
                        <div class="w-auto max-w-2xl mx-auto bg-white shadow-lg rounded-sm border border-gray-200">
                            <header class="px-5 py-4 border-b border-gray-100">
                                <h2 class="font-semibold text-gray-800 text-center">PERSONAS UX</h2>
                            </header>
                            <div class="">
                                <div class="">
                                    <table class="table-auto w-64">
                                        <thead class="text-xs font-semibold uppercase text-gray-400 bg-gray-50">
                                            <tr>
                                                <th class="p-2 whitespace-nowrap">
                                                    <div class="font-semibold  text-center">Id</div>
                                                </th>
                                                <th class="p-2 whitespace-nowrap">
                                                    <div class="font-semibold text-center">Nombre</div>
                                                </th>
                                            </tr>
                                        </thead>
                                        <tbody v-for="(p, contador) in personas" class="text-sm divide-y divide-gray-100">

                                            <tr>
                                                <td class="p-2 whitespace-nowrap">

                                                    <div class="text-center">{{ contador += 1 }} </div>
                                                </td>
                                                <td class="p-2 whitespace-nowrap">
                                                    <button class="text-center" @click="InfoPer(p.id)">{{ p.nombre }}
                                                    </button>

                                                </td>

                                            </tr>



                                        </tbody>
                                    </table>
                                </div>
                            </div>

                        </div>
                    </div>

                </div>
            </div>
        </div>
        <div class="col-span-3">
            <div v-if="mostrar">

                <div class="personaje">
                    <a href="#" class="relative block overflow-hidden rounded-lg border border-gray-100 p-4 sm:p-6 lg:p-8">
                        <span class="absolute inset-x-0 bottom-0 h-2 bg-gradient-to-r from-green-800 "></span>

                        <div class="sm:flex sm:justify-between sm:gap-4">
                            <div>
                                <h3 class="text-lg font-bold text-gray-900 sm:text-xl">
                                    <strong> Nombre: </strong>{{ infoUno.nombre }}
                                </h3>

                                <p class="mt-1 text-xs font-medium text-gray-600">Persona UX</p>
                            </div>


                        </div>

                        <img :src="infoUno.image" alt="" class=" py-3 h-25 w-35 rounded-lg object-cover shadow-sm " />

                        <dl class="mt-6 flex gap-4 sm:gap-6">
                            <div class="flex flex-col-reverse">
                                <dt class="text-sm font-medium text-gray-600"> {{ infoUno.edad }}</dt>
                                <dd class="text-xs text-gray-500">Edad</dd>
                            </div>

                            <div class="flex flex-col-reverse">
                                <dt class="text-sm font-medium text-gray-600"> {{ infoUno.estadoCivil }}</dt>
                                <dd class="text-xs text-gray-500">Estado Civil</dd>
                            </div>


                            <div class="flex flex-col-reverse">
                                <dt class="text-sm font-medium text-gray-600"> {{ infoUno.trabajo }}</dt>
                                <dd class="text-xs text-gray-500">Trabajo</dd>
                            </div>

                            <div class="flex flex-col-reverse">
                                <dt class="text-sm font-medium text-gray-600"> {{ infoUno.residencia }}</dt>
                                <dd class="text-xs text-gray-500">Residencia</dd>
                            </div>

                            <div class="flex flex-col-reverse">
                                <dt class="text-sm font-medium text-gray-600"> {{ infoUno.cita }}</dt>
                                <dd class="text-xs text-gray-500">Cita</dd>
                            </div>

                            <div class="flex flex-col-reverse">
                                <dt class="text-sm font-medium text-gray-600"> {{ infoUno.citaAutor }}</dt>
                                <dd class="text-xs text-gray-500">Autor de la Cita</dd>
                            </div>

                        </dl>
                        <div>
                            <p class="text-xs text-gray-500">Bio:
                            </p>
                            <p class="text-sm font-medium text-gray-600">{{ infoUno.bio }}</p>
                        </div>
                    </a>

                </div>
            </div>
        </div>

</div></template>