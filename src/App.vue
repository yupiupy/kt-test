<template>
	<div id="app">
		<Form @onSubmit="handleSubmit" />
	</div>
</template>

<script>
import Form from '@/components/Form'
//import { response } from 'express';

export default {
		name: 'App',
		components: {
			Form
		},
		methods: {
			handleSubmit(item) {
				// По такой же причине со стороны сервера я не смог отправить запрос (блокировка)

				/*this.axios.post('https://www.ismet.kz/bin/ocp/publicbpms.rest/kzCallBack', {
					mail: item.mail,
					name: item.name,
					organization: item.organization,
					catalog_id: item.catalog_id,
					phone: item.phone,
					server_id: item.server_id,
					recaptchaToken: item.recaptchaToken
				})
				.then(response => console.log(response))
				.catch(e => {
					console.log(e)
				})*/

				/*Access to XMLHttpRequest at 'https://www.ismet.kz/bin/ocp/publicbpms.rest/kzCallBack' 
				from origin 'http://localhost:8080' has been blocked by CORS policy: 
				Response to preflight request doesn't pass access control check: 
				The 'Access-Control-Allow-Origin' header has a value 'https://idp.ismet.kz' that is not equal to the supplied origin.*/

				console.log({
					mail: item.mail,
					name: item.name,
					organization: item.organization,
					catalog_id: item.catalog_id,
					phone: item.phone,
					server_id: item.server_id,
					recaptchaToken: item.recaptchaToken
				})
		}
  }
}
</script>
