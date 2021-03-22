 <template>
 <div id="example">
	<div class="columns is-mobile" v-if="showText">
    <div class="column is-half is-offset-one-quarter box-chat box"> 
		<div class="card">
        <header class="card-header box-chat__header has-text-centered">
		<p class="card-header-title has-text-white ">
		¿Necesitas ayuda?
		</p>
	</header>
	<div class="card-content content-box">
		<div class="content content-text">
			<p>Hola soy KLAY <span><img class="icons" src="~/assets/icons/robotic.svg" alt="logo_twitter"></span> el chatbot se kmote y puedo ayudarte con la información que buscas. </p>
		</div>
		<div class="content content-text">
			<p>¿Quieres que charlemos?</p>
			<button class="button btn-chat">¡Claro, charlemos!</button>
			<button class="button btn-chat">Estoy en busca de trabajo</button>
			<button @click="showPersonal = !showPersonal" class="button btn-chat">Soy Restaurante</button>
		</div>
		<div class="content content-text" v-if="showPersonal">
			<p>Muy bien, nosotros tenemos una amplia gama de perfiles listos para trabajar.
			Para poder continuar necesito que me des un poco de información sobre el perfil que buscas. 
			</p>
			<p>¿Qué vacante deseas cubrir?</p>
			<button class="button btn-chat">Cocinero</button>
			<button @click="showVacante = !showVacante" class="button btn-chat">Auxiliar general</button>
			<button  class="button btn-chat">Barista</button>
		</div>
		<div class="content content-text" v-if="showVacante">
			<p>Perfecto, ¿estás buscando que cuente con experiencia?
			</p>
			<button @click="showExperiencia = !showExperiencia" class="button btn-chat">No importa el nivel de experiencia</button>
			<button  class="button btn-chat">Si, de 1 a 3 años</button>
			<button  class="button btn-chat">Si, de 4 a 7 años</button>
		</div>
		<div class="content content-text" v-if="showExperiencia">
			<p>¿Buscar algún rango de edad?</p>
			<button  class="button btn-chat">Si, mayor de 28 años.</button>
			<button  class="button btn-chat">Si, entre 18 y 35 años.</button>
			<button @click="showNivel = !showNivel" class="button btn-chat">No, ninguno.</button>
		</div>
		<div class="content content-text" v-if="showNivel">
			<p>Perfecto, ya casi estamos en la recta final, por último buscar que tengan algún nivel de estudios?</p>
			<button  class="button btn-chat">Si, bachillerato técnico o preparatoria terminada.</button>
			<button @click="showCandidato = !showCandidato"  class="button btn-chat">No, ninguno.</button>
		</div>
		<div class="content content-text" v-if="showCandidato">
			<p>Excelente! tenemos a los candidatos perfectos para tu negocio.</p>
			<div  id="app">
				<div >
					<ul>
						<li class="result" v-for="(item, index) in result.data">
						<p>Nombre:	{{ item.nombre }} </p>
						<p>Puesto: {{ item.puesto }} </p>
						<p>Edad: {{ item.edad }} </p>
						<p>Experiencia: {{ item.experiencia }} años </p>
						<p>Preparatoria: {{ item.preparatoria }} </p>
						<p>Id: {{ item._id }}</p>
						<img class="icons" src="~/assets/icons/pdf.svg" alt="image_hero">
						</li>
					</ul>
					
				</div>
			</div>
		</div>
			</div>
			<footer class="card-footer">
				<input class="input" type="text" placeholder="">
				<a class="button btn_send">
					Enviar
				</a>
			</footer>
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
.btn-chat{
	border: 1px solid #EF6C00;
}
.btn_send{
background-color: #4FB1BD;
color: #ffffff;
}
.btn_send:hover{
color: #E4FEE4;
}
.box{
	border-style: none;
	font-size: 16px;
	color: #ffffff; 
	border-radius: 5px;  
	padding: 8px 15px;
	position: fixed;
	bottom: 150px;
	right: 40px;
	box-shadow: 0px 8px 15px rgba(239,108, 0, 0.1);
	z-index: 99;
}
.content-box{
	max-height: 400px;
	overflow:scroll;
}
.box-chat__header{
	background-color:#4FB1BD;
}
.content-text{
	background-color:#F5F7F9;
	padding:15px;
	font-size: 14px;
	border-radius: 10px;
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
.result{
	border: 1px solid #EF6C00;
	background-color: #ffffff; 
	padding: 20px;
	list-style: none;
	border-radius: 15px;
}
.icons{
	width: 30px;
	height: 30px;
}
.list_candidato{
	margin-top: 30px;
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
