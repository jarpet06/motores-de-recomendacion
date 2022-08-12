<script setup>
import { ref } from 'vue';

const sections = ref([
	{
		id: 0,
		type: 'title',
		title: 'Motores de Recomendación',
		subtitle: 'Por Máximo Giqueaux, Jared Peter, Giovanni Gerber',
		current: true
	},
	{
		id: 1,
		type: 'presentation',
		title: 'Introducción',
		text: `
			<ul class="list-disc leading-8 ml-5">
				<li>Proporcionan sugerencias de elementos que pueden interesar a los usuarios</li>
				<li>Permiten a los desarrolladores de algoritmos predecir si a los consumidores les gustará o no</li>
				<li>La aparición de herramientas Open Source (herramientas de libre acceso para todos) incentivan la creación de motores de recomendación.</li>
			</ul>
		​`,
		current: false
	},
	{
		id: 2,
		type: 'presentation',
		title: 'Motores de Recomendación y el Negocio​',
		text: `
			<p>Los motores de recomendación logran uno de los principales objetivos de las empresas, fidelizar el mayor número de consumidores.​ <br><br>
			Hay dos tipos de algoritmos de recomendación:</p>
			<ul class="mt-1 ml-5 list-disc">
				<li><em>Predicción del Problema</em>: se establece una clasificación con los valores que introduce un usuario al conseguir un producto<br></li>
				<li><em>Ranking del Problema:</em> se clasifican las preferencias del usuario</li>
			</ul>
		​`,
		current: false
	},
	{
		id: 3,
		type: 'title',
		title: 'Tipos de Motores de Recomendación',
		current: false
	},
	{
		id: 4,
		type: 'presentation',
		title: 'Colaborativos',
		text: `
			<p>Su principal fuente de datos son las preferencias (ratings) aportadas por los diferentes usuarios. Estos datos son utilizados como estratega de recomendación.<br><br>
			Hay dos métodos que se usan para predecir los valores que los usuarios no mostraran preferencia:</p>
			<ul class="mt-1 ml-5 list-disc">
				<li><em>"Memory Based Methods":</em> las calificaciones de combinaciones usuario-producto son establecidas en base a sus vecinos.<br></li>
				<li><em>"Model Based Methods":</em> se utiliza la matriz de valoraciones para crear diferentes modelos con algoritmos de “machine learning” para realizar la recomendación</li>
			</ul>
		​`,
		current: false
	},
	{
		id: 5,
		type: 'presentation',
		title: 'Filtrado Basado en Contenido',
		text: `
			El sistema recomienda ítems al usuario basándose exclusivamente en su experiencia pasada. Se recomiendan ítems de características similares a los que reaccionó positivamente el usuario activo.<br><br>
			<span>Se trabaja con la información que se obtiene de los atributos de usuarios y productos como perfiles o palabras clave.</span>
		`,
		current: false
	}
]);

const changeSection = (section) => {
	section.current = false;
	sections.value[section.id+1].current = true;
}
</script>

<template>
	<div class="h-screen relative bg-[url('./hero.png')] bg-cover bg-no-repeat flex justify-center items-center">
		<div class="w-screen h-screen absolute top-0 left-0 backdrop-blur-sm z-10"></div>
		<div v-for="section, i, elements in sections">
			<div v-if="section.current" class="relative z-20 bg-white rounded-2xl py-8 px-10 shadow-2xl h-96 w-[50rem]">
				<div v-if="section.type === 'title'" class="flex flex-col justify-center items-center h-full">
					<h1 class="text-5xl font-bold text-center">{{ section.title }}</h1>
					<h4 v-if="section.subtitle" class="text-xl mt-3 font-light">{{ section.subtitle }}</h4>
					<button
						@click="() => changeSection(section)"
						class="mt-5 px-6 py-2 rounded-lg shadow-sm bg-red-400 focus:ring-2 focus:ring-red-300 focus:ring-offset-2 text-white">
						Siguiente
					</button>
				</div>
				<div v-else>
					<h2 class="text-4xl font-bold">{{ section.title }}</h2>
					<div class="mt-3" v-html="section.text"></div>
					<button
						@click="() => changeSection(section)"
						class="absolute bottom-10 left-10 px-6 py-2 rounded-lg shadow-sm bg-red-400 focus:ring-2 focus:ring-red-300 focus:ring-offset-2 text-white">
						Siguiente
					</button>
				</div>
			</div>
		</div>
	</div>
</template>