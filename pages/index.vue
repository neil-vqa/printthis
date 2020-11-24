<template>
  <div class="mx-auto p-10 h-screen max-w-screen-xl">
    <div class="grid grid-cols-2 gap-10 h-full">
    
    <!-- input data -->
    	<div class="border-2 border-gray-500 p-5 overflow-auto">
    		<form @submit.prevent="generateReport">
    			<div class="px-4 w-full">
				    <div class="mb-2">
				      <label for="name" class="input-label">Name</label>
				      <input v-model="name" id="name" type="text" class="input-box">
				    </div>
				    <div class="mb-2">
				      <label for="required" class="input-label">Age</label>
				      <input v-model="age" type="number" class="input-box">
				    </div>
				  	<div class="mb-2">
				      <label for="address" class="input-label">Address</label>
				      <input v-model="address" id="address" type="text" class="input-box">
				    </div>
				    <div class="mb-2">
				      <label for="image" class="input-label">image</label>
				      <input v-model="image" id="image" type="text" class="input-box">
				    </div>
				    <div class="my-10">
				    	<button type="submit" class="px-4 py-2 bg-gray-700 hover:bg-gray-900 text-white">Generate Report</button>
				    </div>
				  </div>
    		</form>
    	</div>
    	
    <!-- preview -->	
    	<div class="border-2 border-gray-500 overflow-auto">
    		<client-only>
					<vue-html2pdf 
						:show-layout="true"
						:float-layout="false"
						:enable-download="true"
						:manual-pagination="true"
						filename="Report"
						pdf-orientation="portrait"
						pdf-content-width="100%"
						pdf-format="letter"
						ref="html2Pdf">
						  <section slot="pdf-content">
						  	<div class="p-5">
						  		<h1 class="text-lg text-center">Welcome</h1>
						  		<h1 class="text-lg">{{ name }}</h1>
						  		<h1 class="text-lg">{{ age }}</h1>
						  		<h1 class="text-lg">{{ address }}</h1>
						  		<img :src="image">
						  	</div>
						  </section>
					</vue-html2pdf>
				</client-only>
    	</div>
    	
    </div>
  </div>
</template>

<script>

export default {
	data() {
		return {
			name: '',
			age: '',
			address: '',
			image: '',
		}
	},
	methods: {
		generateReport() {
        this.$refs.html2Pdf.generatePdf()
    }
	},
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/

.input-box {
	@apply block w-full border border-gray-400 py-1 px-4 text-gray-700 text-base;
}

.input-label {
	@apply text-sm leading-7 text-gray-700 uppercase font-bold;
}

</style>
