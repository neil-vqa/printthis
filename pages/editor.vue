<template>
  <div class="mx-auto p-10 h-screen max-w-screen-xl">
    <div class="grid grid-cols-2 gap-10 h-full">
    
    <!-- input data -->
    	<div class="border-2 border-gray-500 p-5 overflow-auto">
    		<div>
    			<div class="px-4 w-full">
    				<div class="grid grid-cols-2 gap-2">
						  <div class="mb-2">
						    <label for="name" class="input-label">Name</label>
						    <input v-model="name" id="name" type="text" class="input-box">
						  </div>
						  <div class="mb-2">
						    <label for="position" class="input-label">Position</label>
						    <input v-model="position" id="position" type="text" class="input-box">
						  </div>
							<div class="mb-2">
						    <label for="division" class="input-label">Division</label>
						    <input v-model="division" id="division" type="text" class="input-box">
						  </div>
						  <div class="mb-2">
						    <label for="school" class="input-label">School</label>
						    <input v-model="school" id="school" type="text" class="input-box">
						  </div>
						  <div class="mb-2">
						    <label for="submitted" class="input-label">Date Submitted</label>
						    <input v-model="submitted" id="submitted" type="text" class="input-box">
						  </div>
						  <div class="mb-2">
						    <label for="verifier-name" class="input-label">Verifier Name</label>
						    <input v-model="verifierName" id="verifier-name" type="text" class="input-box">
						  </div>
						  <div class="mb-2">
						    <label for="verifier-position" class="input-label">Verifier Position</label>
						    <input v-model="verifierPosition" id="verifier-position" type="text" class="input-box">
						  </div>
				    </div>
				    
				    <!-- repeatable activities -->
				    <div class="input-label">Activities</div>
				    <div class="mb-2 grid grid-cols-2 gap-2 bg-gray-200 p-2" v-for="activity in activities">
				    	<div>
				    		<label for="date" class="text-xs text-gray">Date</label>
				      	<input v-model="activity.date" id="date" type="text" class="input-box">
				    	</div>
				    	<div>
				    		<label for="output" class="text-xs text-gray">Output</label>
				      	<input v-model="activity.output" id="output" type="text" class="input-box">
				    	</div>
				    	<div>
				    		<label for="time-in" class="text-xs text-gray">Time-in</label>
				      	<input v-model="activity.time.in" id="time-in" type="text" class="input-box">
				    	</div>
				    	<div>
				    		<label for="time-out" class="text-xs text-gray">Time out</label>
				      	<input v-model="activity.time.out" id="time-out" type="text" class="input-box">
				    	</div>
				    </div>
				    <button @click="addActivity" class="px-4 py-2 mb-2 bg-gray-700 hover:bg-gray-900 text-white text-xs">Add more</button>
				    
				    <!-- repeatable images -->
				    <div class="input-label">Images</div>
				    <div class="mb-2" v-for="image in images">
				      <label for="image" class="text-xs text-gray">Link</label>
				      <input v-model="image.pic" id="image" type="text" class="input-box">
				    </div>
				    <button @click="addImage" class="px-4 py-2 mb-2 bg-gray-700 hover:bg-gray-900 text-white text-xs">Add more</button>
				    
				    <div class="my-10">
				    	<button @click="generateReport" class="px-4 py-2 bg-gray-700 hover:bg-gray-900 text-white">Download Report</button>
				    </div>
				  </div>
    		</div>
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
						pdf-format="a4"
						ref="html2Pdf">
						   <section slot="pdf-content">
						  	<div class="p-10">
						  		<h1 class="text-base mb-10">Enclosure No. 2 to DMNo. 043, s. 2020</h1>
						  		<h1 class="text-base font-bold uppercase text-center mb-5">INDIVIDUAL WORKWEEK ACCOMPLISHMENT REPORT</h1>
						  		<div class="grid grid-cols-2 mb-10">
						  			<div>
						  				<p class="text-base whitespace-pre">Name of Personnel:	{{ name }}</p>
						  				<p class="text-base whitespace-pre">Position:			{{ position }}</p>
						  			</div>
						  			<div>
						  				<p class="text-base whitespace-pre">Division:	{{ division }}</p>
						  				<p class="text-base whitespace-pre">School:		{{ school }}</p>
						  			</div>
						  		</div>
						  		<table class="table-fixed mb-16">
										<thead>
											 <tr>
												<th class="px-3 py-2 w-1/4 border border-black">Actual Days of Attendance to Work</th>
												<th class="px-3 py-2 w-1/4 border border-black">Actual Time Log</th>
												<th class="px-3 py-2 w-1/2 border border-black">Actual Accomplishments/Output</th>
											</tr>
										</thead>
										<tbody>
											<tr v-for="activity in activities">
												<td class="px-3 py-2 text-center border border-black" v-if="activity.date">{{ activity.date }}</td>
												<td class="px-3 py-2 text-center border border-black" v-if="activity.time.in">
													Time-in: {{ activity.time.in }} <br />
													Time out: {{ activity.time.out }}
												</td>
												<td class="px-3 py-2 text-center border border-black" v-if="activity.output">{{ activity.output }}</td>	
											</tr>
										</tbody>
									</table>
									<div class="text-center text-sm">
										<p class="mb-4 text-base">Submitted by:</p>
										<p class="uppercase underline font-bold text-base">{{ name }}</p>
										<p><i>{{ position }}</i></p>
										<p><i>Date: {{ submitted }}</i></p>
										<br /><br />
										<p class="mb-4 text-base">Verified by:</p>
										<p class="uppercase underline font-bold text-base">{{ verifierName }}</p>
										<p><i>{{ verifierPosition }}</i></p>
										<p><i>Date: {{ submitted }}</i></p>
									</div>
						  		<div class="flex justify-center space-x-5 mt-10">
						  			<div v-for="image in images"><img :src="image.pic" class="h-32"></div>
						  		</div>
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
	layout: 'general',
	data() {
		return {
			name: '',
			position: '',
			division: '',
			school: '',
			submitted: '',
			verifierName: '',
			verifierPosition: '',
			activities: [{date: '', time:{in: '', out: ''}, output:''}],
			images: [{pic: ''}],
		}
	},
	methods: {
		addActivity() {
			this.activities.push({date: '', time:{in: '', out: ''}, output:''});
		},
		addImage() {
			this.images.push({pic: ''});
		},
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
