 <template>
 <div id="example">
	 <div class="box" v-if="showText">
	<div class="columns is-mobile">
    <div class="column is-half is-offset-one-quarter box-chat"> 
		<div class="card">
        <header class="card-header box-chat__header has-text-centered">
		<p class="card-header-title has-text-white ">
		¿Necesitas ayuda?
		</p>
	</header>
	<div class="card-content">
		<div class="content content-text">
			<p>Hola soy KLAY el chatbot se kmote y puedo ayudarte con la información que buscas. </p>
		</div>
		<div class="content content-text">
			<p>¿Quieres que charlemos?</p>
			<button class="button">¡Claro, charlemos!</button>
			<button class="button">Estoy en busca de trabajo</button>
			<button @click="showPersonal = !showPersonal" class="button">Soy Restaurante</button>
		</div>
		<div class="content content-text" v-if="showPersonal">
			<p>Muy bien, nosotros tenemos una amplia gama de perfiles listos para trabajar.
			Para poder continuar necesito que me des un poco de información sobre el perfil que buscas. 
			</p>
			<p>¿Qué vacante deseas cubrir?</p>
			<button class="button">Cocinero</button>
			<button @click="showVacante = !showVacante" class="button">Auxiliar general</button>
			<button  class="button">Barista</button>
		</div>
		<div class="content content-text" v-if="showVacante">
			<p>Perfecto, ¿estás buscando que cuente con experiencia?
			</p>
			<button @click="showExperiencia = !showExperiencia" class="button">No importa el nivel de experiencia</button>
			<button  class="button">Si, de 1 a 3 años</button>
			<button  class="button">Si, de 4 a 7 años</button>
		</div>
		<div class="content content-text" v-if="showExperiencia">
			<p>¿Buscar algún rango de edad?</p>
			<button  class="button">Si, mayor de 28 años.</button>
			<button  class="button">Si, entre 18 y 35 años.</button>
			<button @click="showNivel = !showNivel" class="button">No, ninguno.</button>
		</div>
		<div class="content content-text" v-if="showNivel">
			<p>Perfecto, ya casi estamos en la recta final, por último buscar que tengan algún nivel de estudios?</p>
			<button  class="button">Si, bachillerato técnico o preparatoria terminada.</button>
			<button @click="showCandidato = !showCandidato"  class="button">No, ninguno.</button>
		</div>
		<div class="content content-text" v-if="showCandidato">
			<p>Excelente! tenemos a los candidatos perfectos para tu negocio.</p>
			<div id="app">
				<p>
					<ul>
						<li v-for="(item, index) in result.data">
						<p>Nombre:	{{ item.nombre }} </p>
						<p>Puesto: {{ item.puesto }} </p>
						<p>Edad: {{ item.edad }} </p>
						<p>Experiencia: {{ item.experiencia }} años </p>
						<p>Preparatoria: {{ item.preparatoria }} </p>
						<p>Id: {{ item.id }} años </p>
						</li>
					</ul>
					{{ result.data }}
				</p>
			</div>
		</div>
			</div>
			<footer class="card-footer">
				<input class="input" type="text" placeholder="">
				<a class="button is-info">
					Enviar
				</a>
			</footer>
		</div>
		</div>
		</div>

	</div>
		<button @click="showText = !showText" class="btn-flotante" >
			<img src="~/assets/icons/chat.svg" alt="image_hero">
		</button>
	</div>
</template> 

<script lang="ts">
import Vue from 'vue'
import axios from 'axios'

export default{
	data: () => {
		return {
			result: null,
			showText:false,
			showPersonal:false,
			showVacante:false,
			showExperiencia:false,
			showEdad:false,
			showNivel:false,
			showCandidato:false,
		}
	},
		created() {
    axios.get("https://kmote.mx/devtest/").then((result) => {
      this.result = result.data;
    })
  }
};
</script>

<style>

.box-chat__header{
	background-color:#4FB1BD;
}
.content-text{
	background-color:#F5F7F9;
	padding:15px;
	font-size: 14px;
	border-radius: 10px;
}
.button{
	border: 1px solid #EF6C00;
}
.btn-flotante {
	border-style: none;
	font-size: 16px;
	text-transform: uppercase; 
	font-weight: bold; 
	color: #ffffff; 
	border-radius: 5px; 
	letter-spacing: 2px; 
	background-color: #EF6C00; 
	padding: 8px 15px;
	position: fixed;
	bottom: 40px;
	right: 40px;
	transition: all 300ms ease 0ms;
	box-shadow: 0px 8px 15px rgba(0, 0, 0, 0.1);
	z-index: 99;
}
.btn-flotante:hover {
	background-color: #E4FEE4; 
	box-shadow: 0px 15px 20px rgba(0, 0, 0, 0.3);
	transform: translateY(-7px);
}
@media only screen and (max-width: 600px) {
 	.btn-flotante {
		font-size: 14px;
		padding: 5px 10px;
		bottom: 20px;
		right: 20px;
	}
}
</style>
