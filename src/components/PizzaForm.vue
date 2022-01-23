<template>
	<Message :msg="msg" v-show="msg" />
	<form id="form" @submit="createProduct">
		<div class="input-wrapper">
			<label for="name">Client Name</label>
			<input
				type="text"
				id="name"
				name="name"
				v-model="name"
				placeholder="Type your name.."
			/>
		</div>
		<div class="input-wrapper">
			<label for="crust">Choose type of crust</label>
			<select name="crust" id="crust" v-model="crust">
				<option value="">Select crust</option>
				<option v-for="crust in crusts" :key="crust.id" :value="crust.type">
					{{ crust.type }}
				</option>
			</select>
		</div>
		<div class="input-wrapper">
			<label for="meat">Choose the type of meat</label>
			<select name="meat" id="meat" v-model="meat">
				<option value="">Select meat</option>
				<option v-for="meat in meats" :key="meat.id" :value="meat.type">
					{{ meat.type }}
				</option>
			</select>
		</div>
		<div id="optionas-wrapper" class="input-wrapper">
			<label id="optinal-title" for="item">Select your options</label>
			<div
				class="checkbox-wrapper"
				v-for="option in optionsdatas"
				:key="option.id"
			>
				<input
					type="checkbox"
					name="options"
					v-model="options"
					:value="option.type"
				/>
				<span>{{ option.type }}</span>
			</div>

			<div class="input-wrapper">
				<input type="submit" class="submit-btn" value="Create a pizza" />
			</div>
		</div>
	</form>
</template>

<script>
import Message from './Message.vue';
export default {
	name: 'PizzaForm',
	components: {
		Message
	},
	data() {
		return {
			meats: null,
			crusts: null,
			optionsdatas: null,
			name: null,
			options: [],
			crust: null,
			meat: null,
			msg: null
		};
	},
	methods: {
		async getIngredients() {
			const req = await fetch('http://localhost:3000/ingredients');
			const data = await req.json();

			this.meats = data.meats;
			this.crusts = data.crusts;
			this.optionsdatas = data.options;

			console.log(data.crusts);
		},
		async createProduct(e) {
			e.preventDefault();
			const data = {
				name: this.name,
				meat: this.meat,
				status: 'Requested',
				options: Array.from(this.options),
				crust: this.crust
			};
			const jsonData = JSON.stringify(data);
			const req = await fetch('http://localhost:3000/pizzas', {
				method: 'POST',
				headers: { 'Content-Type': 'application/json' },
				body: jsonData
			});
			const res = await req.json();
			console.log(res);
			//	console.log(data);

			// show an message
			this.msg = `Congratulations your order N ${res.id} has been placed`;

			// hidden message alert
			setTimeout(() => {
				this.msg = '';
			}, 2000);
			//setTimeout(() => (this.msg = ''), 3000);

			//clean input field
			this.name = '';
			this.crust = '';
			this.meat = '';
			this.options = '';
		}
	},
	mounted() {
		this.getIngredients();
	}
};
</script>

<style scoped>
#form {
	max-width: 31.25rem;
	margin: 0 auto;
}
.input-wrapper {
	display: flex;
	flex-direction: column;
	margin-bottom: 1.5rem;
}
label {
	font-weight: bold;
	margin-bottom: 1rem;
	color: #222;
	padding: 0.5rem 0.8rem;
	border-left: 0.4rem solid salmon;
}
input,
select {
	padding: 0.5rem 0.8rem;
	width: 18.75rem;
}
#optionas-wrapper {
	flex-direction: row;
	flex-wrap: wrap;
}
#optinal-title {
	width: 100%;
}
.checkbox-wrapper {
	display: flex;
	align-items: flex-end;
	width: 50%;
	margin-bottom: 1.25rem;
}
.checkbox-wrapper span,
.checkbox-wrapper input {
	width: auto;
}
.checkbox-wrapper span {
	margin-left: 0.6rem;
	font-weight: bold;
}
.submit-btn {
	background: #418a4d;
	color: hsl(30, 100%, 100%);
	font-weight: bold;
	padding: 0.6rem;
	font-size: 1rem;
	border-radius: 0.5rem;
	margin: 0 auto;
	cursor: pointer;
	transition: 0.5s;
	outline: none;
}
.submit-btn:hover {
	background: transparent;
	color: #0e0a0a;
}
</style>
