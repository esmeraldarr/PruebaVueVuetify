<template>
    <div>
		<Navbar/>

		<v-container>
			<v-breadcrumbs :items="items"></v-breadcrumbs>
			<v-layout wrap>
				<v-flex xs12 md12>
					<div class="text-courses">
						<h1>Cursos</h1>
					</div>
				</v-flex>
				<v-flex xs12 md12>
					<div class="rectangle-206 base-primary"></div>
				</v-flex>
			</v-layout>
			<v-layout class="mt-12" justify-center>
				<v-flex xs12 md6>
					<div class="base-secondary">
						<p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. 
							Excepturi incidunt magnam aliquam quas repudiandae iste fugit placeat doloribus 
							perspiciatis corporis ex eum vel tempore assumenda totam ratione, illum cum voluptas!
						</p>
					</div>
				</v-flex>
			</v-layout>	
		</v-container>

		<!-- <Searcher/> -->
		<div class="rectangle graysLight">
			<v-container>
				<v-layout>
					<v-flex xs2 md1>
						<v-icon>mdi-format-list-checkbox</v-icon>
					</v-flex>
					<v-flex xs6 md3 justify-start>
						<p>#numero Colecciones disponibles para tu selección</p>
					</v-flex>
				</v-layout>
				<v-layout wrap class="mt-12" md12>
					<v-flex v-for="card in showCards" :key="card.num" md4 >
						<v-card class="courses-cards gray-2">
							<v-img
								class="white--text align-end"
								height="90%"
								:src="card.imageUrl"
								>
							</v-img>
							<v-card-actions>
								<v-dialog
									:v-model="card.multiverseid"
									width="500"
									>
									<template v-slot:activator="{ on, cardDetail }">
										<a style="color:white;" v-bind="cardDetail" v-on="on">{{ card.name }}</a>
										
									</template>

									<v-card>
										<v-card-title class="text-h5 grey lighten-2">
										Artista {{ card.artist }}
										</v-card-title>

										<v-card-text>
											<h6>Poder :</h6><p>{{ card.power }}</p>
											<h6>Descripción :</h6><p>{{ card.text }}</p>
										</v-card-text>
									</v-card>
								</v-dialog>
							</v-card-actions>
						</v-card>
					</v-flex>
				</v-layout>	
			</v-container>
		</div>
		
		<Footer/>
    </div>
</template>

<script>
import Navbar from '@/components/Navbar.vue'
import Footer from '@/components/Footer.vue'
import axios from 'axios'
// import Searcher from '@/components/Searcher.vue'

export default {
	name: 'Layout',
	components: {
		Navbar,
		Footer
		// Searcher
	},
	data() {
		return {
			cards: null,
			items: [
				{
				text: 'Inicio',
				disabled: true,
				href: '',
				},
				{
				text: 'Cursos',
				disabled: false,
				href: '',
				}
			]   
		}
	},
computed: {
	showCards () { 
		const { cards } = this;
		return cards;
	}
},
mounted () {
	axios
	.get('https://api.magicthegathering.io/v1/cards')
	.then(response => (this.cards = response.data.cards))
}
}
</script>
