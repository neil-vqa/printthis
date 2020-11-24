<template>
  <div class="home-screen">
    <div class="h-screen w-full flex flex-col justify-center items-center">
			<div class="welcome w-11/12 sm:w-auto text-center px-6 sm:px-10 py-20 flex flex-col justify-center items-center space-y-5 text-white">
				<div class="flex space-x-2 items-center">
					<svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-file-like" width="60" height="60" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round">
						<path stroke="none" d="M0 0h24v24H0z" fill="none"/>
						<rect x="3" y="16" width="3" height="5" rx="1" />
						<path d="M6 20a1 1 0 0 0 1 1h3.756a1 1 0 0 0 .958 -.713l1.2 -3c.09 -.303 .133 -.63 -.056 -.884c-.188 -.254 -.542 -.403 -.858 -.403h-2v-2.467a1.1 1.1 0 0 0 -2.015 -.61l-1.985 3.077v4z" />
						<path d="M14 3v4a1 1 0 0 0 1 1h4" />
						<path d="M5 12.1v-7.1a2 2 0 0 1 2 -2h7l5 5v11a2 2 0 0 1 -2 2h-2.3" />
					</svg>
				</div>
				<h1 class="text-4xl sm:text-6xl font-semibold">Welcome!</h1>
				<p class="text-base sm:text-2xl pb-10">Mama's Document Editor</p>
				<NuxtLink to="/editor" class="admin text-base p-5">Proceed to Editor</NuxtLink>
			</div>
		</div>
  </div>
</template>

<script>
export default {
	layout: 'general',
	
}
</script>

<style scoped>
.home-screen {
	background: #68d391;
}

.welcome {
	height: 80%;
	border-radius: 50px;
	background: #68d391;
	box-shadow:  20px 20px 60px #58b37b, 
		           -20px -20px 60px #78f3a7;
}

.admin {
	border-radius: 50px;
	background: linear-gradient(145deg, #6fe29b, #5ebe83);
	box-shadow:  16px 16px 43px #51a571, 
		           -16px -16px 43px #7fffb1;
}

.admin:hover {
	color: #555;
	border-radius: 50px;
	background: #68d391;
	box-shadow:  16px 16px 43px #51a571, 
		           -16px -16px 43px #7fffb1;
}
















</style>




