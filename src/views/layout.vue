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
						<v-card>
							<v-card-title>{{card.num}}</v-card-title>
							<v-card-subtitle>{{card.nombre}}</v-card-subtitle>
						</v-card>
					</v-flex>
					<v-flex xs12>
						<div class="text-center">
							<v-pagination v-model="page" :length="length"></v-pagination>
						</div>
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
		page:1,
      length:2,
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
      ],
		cards: [
			{"num": 1, "nombre": "n1"},
			{"num": 2, "nombre": "n2"},
			{"num": 3, "nombre": "n3"},
			{"num": 4, "nombre": "n4"},
			{"num": 5, "nombre": "n5"},
			{"num": 6, "nombre": "n6"},
			{"num": 7, "nombre": "n7"},
			{"num": 8, "nombre": "n8"}
		]   
		}
	},
	computed: {
  
    showCards () { 
    
      const { page, length, cards } = this;
      const number = Math.ceil(cards.length / length);
      return cards.slice((page - 1) * number, page * number);
    
    }
  
  }
}
</script>
