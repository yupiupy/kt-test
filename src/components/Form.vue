<template>
	<div>
		<form id="form" @submit.prevent="onSubmit" novalidate>
			<label for="email">Введите ваш E-mail</label>
			<input type="email" v-model="mail" id="email">
			<label for="name"> Введите ваше имя</label>
			<input type="name" v-model="name" id="name">
			<label for="organization">Укажите организацию</label>
			<input type="text" v-model="organization" id="organization">
			<label for="catalog_id">Выберите услугу</label>
			<input type="text" v-model="catalog_id" id="catalog_id">
			<label for="phone">Введите ваш телефон</label>
			<input type="phone" v-model="phone" id="phone">
			<label for="servers">Выберите регион</label>
			<select size="1" v-model="server_id" id="servers">
				<ServerId v-for="el in servers" :key="el.id" :item="el" />
			</select>
			<label for="recaptchaToken">Введите капчу</label>
			<input type="text" v-model="recaptchaToken" id="recaptchaToken">
			<button type="submit">submit</button>
		</form>
	</div>
</template>

<script>
import ServerId from '@/components/ServerId.vue'
export default {
	components: {
		ServerId
	},
	data() {
		return {
			mail: '',
			name: '',
			organization: '',
			catalog_id: '',
			phone: '',
			server_id: '',
			recaptchaToken: '',
			servers: []
		}
	},
	methods: {
		onSubmit() {
				this.$emit('onSubmit', {
					mail: this.mail,
					name: this.name,
					organization: this.organization,
					catalog_id: this.catalog_id,
					phone: this.phone,
					server_id: this.server_id,
					recaptchaToken: this.recaptchaToken
				})
				this.mail = '',
				this.name = '',
				this.organization = '',
				this.catalog_id = '',
				this.phone = '',
				this.server_id = '',
				this.recaptchaToken = ''
		}
	},
	mounted() {
			//Я не смог получить данные с вашего ресурса (блокировка со стороны сервера):

			//this.axios.get('https://www.ismet.kz/bin/ocp/publicbpms.rest/reference/kt_cb_server')
			this.axios.get('https://api.privatbank.ua/p24api/pubinfo?json&exchange&coursid=5')
				.then(responce => {
					this.servers = responce.data
				})
			
			/*
			Access to XMLHttpRequest at 'https://www.ismet.kz/bin/ocp/publicbpms.rest/reference/kt_cb_server' 
			from origin 'http://localhost:8080' has been blocked by CORS policy:
			The 'Access-Control-Allow-Origin' header has a value 'https://idp.ismet.kz' that is not equal to the supplied origin*/
	}
}
</script>
