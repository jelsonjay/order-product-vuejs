<template>
	<div id="burger-table" v-if="pizzas">
		<Message :msg="msg" v-show="msg" />
		<div>
			<div id="burger-table-heading">
				<div class="order-id">ID:</div>
				<div>Cliente:</div>
				<div>Crust:</div>
				<div>Meat:</div>
				<div>Options:</div>
				<div>Actions:</div>
			</div>
		</div>
		<div id="burger-table-rows">
			<div class="burger-table-row" v-for="pizza in pizzas" :key="pizza.id">
				<div class="order-number">{{ pizza.id }}</div>
				<div>{{ pizza.name }}</div>
				<div>{{ pizza.crust }}</div>
				<div>{{ pizza.meat }}</div>
				<div>
					<ul v-for="(option, index) in pizza.options" :key="index">
						<li>{{ option }}</li>
					</ul>
				</div>
				<div>
					<select
						name="status"
						class="status"
						@change="updatePizza($event, pizza.id)"
					>
						<option
							:value="s.type"
							v-for="s in status"
							:key="s.id"
							:selected="pizza.status == s.type"
						>
							{{ s.type }}
						</option>
					</select>
					<button class="delete-btn" @click="deletePizza(pizza.id)">
						Delete
					</button>
				</div>
			</div>
		</div>
	</div>
	<div v-else>
		<h2>Não há pedidos no momento!</h2>
	</div>
</template>
<script>
import Message from './Message.vue';
export default {
	name: 'AdminTwo',
	components: {
		Message
	},
	data() {
		return {
			pizzas: null,
			pizza_id: null,
			status: [],
			msg: null
		};
	},
	methods: {
		async getPedidos() {
			const req = await fetch('http://localhost:3000/pizzas');
			const data = await req.json();
			this.pizzas = data;
			// Resgata os status de pedidos
			this.getStatus();
		},
		async getStatus() {
			const req = await fetch('http://localhost:3000/status');
			const data = await req.json();
			this.status = data;
		},
		async deletePizza(id) {
			const req = await fetch(`http://localhost:3000/pizzas/${id}`, {
				method: 'DELETE'
			});
			const res = await req.json();

			// show an message
			this.msg = `Order removed successfully!`;
			// hidden message alert
			setTimeout(() => {
				this.msg = '';
			}, 2000);

			this.getPedidos();
			console.log(res);
		},
		async updatePizza(event, id) {
			const option = event.target.value;
			const dataJson = JSON.stringify({ status: option });
			const req = await fetch(`http://localhost:3000/pizzas/${id}`, {
				method: 'PATCH',
				headers: { 'Content-Type': 'application/json' },
				body: dataJson
			});
			const res = await req.json();

			// show an message
			this.msg = `The order N ${res.id} has been updated ${res.status}`;
			// hidden message alert
			setTimeout(() => {
				this.msg = '';
			}, 2000);

			console.log(res);
		}
	},
	mounted() {
		this.getPedidos();
	}
};
</script>

<style scoped>
#burger-table {
	max-width: 1200px;
	margin: 0 auto;
}
#burger-table-heading,
#burger-table-rows,
.burger-table-row {
	display: flex;
	flex-wrap: wrap;
}
#burger-table-heading {
	font-weight: bold;
	padding: 12px;
	border-bottom: 3px solid #333;
}
.burger-table-row {
	width: 100%;
	padding: 12px;
	border-bottom: 1px solid #ccc;
}
#burger-table-heading div,
.burger-table-row div {
	width: 19%;
}
#burger-table-heading .order-id,
.burger-table-row .order-number {
	width: 5%;
}
select {
	padding: 12px 6px;
	margin-right: 12px;
}
.delete-btn {
	background-color: #f13535;
	color: #f7f5f2;
	font-weight: bold;
	border: 0.1rem solid #ee0909;
	padding: 10px;
	font-size: 16px;
	margin: 0 auto;
	cursor: pointer;
	transition: 0.5s;
	border-radius: 0.5rem;
}

.delete-btn:hover {
	background-color: transparent;
	color: #222;
}
li {
	list-style: none;
}
</style>
