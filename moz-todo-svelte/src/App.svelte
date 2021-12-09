<script>
//logic goes here
let products = [{number:1, name:"Pink Drink", image: "https://hips.hearstapps.com/del.h-cdn.co/assets/17/15/2560x3965/gallery-1491914852-pink-drink-2017.jpg?resize=480:*" , price: 4, quantity: 1},
				{number:2, name: "Matcha Creme Frappuccino" , image: "https://th.bing.com/th/id/OIP.5uSa-4_5D0rSMEcxe60UdwHaK8?pid=ImgDet&w=206&h=304&c=7&dpr=1.25", price: 4, quantity: 1},
				{number:3, name: "Iced Caramel Macchiato with Oat Milk" , image: "https://i.pinimg.com/originals/1a/ed/50/1aed50bd212c1a3a0c52cacd31daf35c.jpg", price: 5, quantity: 1},
			]
let cart = []
//this function receive products chosen by the user and push it to the cart
const addToCart = (product) =>{
	for(let item of cart){
		//if same items added to the cart multiple times
		if(item.number == product.number){
			//quantity increases
			product.quantity += 1
			cart = cart
			return
		}
	}
	//only display the quantity of the cart item
	//avoid multiple items keep adding to the cart array
	cart = [...cart,product]
}
//able to remove items from the cart array
const removeItem = (product) =>{
	for(let item of cart){
		if(item.number == product.number){
			if(product.quantity>1){
				product.quantity -= 1
				cart = cart
			}else{
				cart = cart.filter((cartItem) => cartItem != product)
			}
			return
		}
	}
}
//able to add items from the cart array
const addItem = (product) => {
		for(let item of cart) {
			if(item.number === product.number) {
				item.quantity += 1
				cart = cart
				return
			}
		}
	}
	//
	$: total = cart.reduce((sum, item) => sum + item.price * item.quantity, 0)
</script>

<main>
	<h1>Welcome to Petite_Starbucks!</h1>
</main>

<p>There are {cart.length} items in your cart</p>

<div class="product-list">
	{#each products as product}
	<div>
		<div class="image" style="background-image: url({product.image})"></div>
	<h4>{product.name}</h4>
	<p>${product.price}</p>
	<button on:click={() => addToCart(product)}>Add to cart</button>
	</div>
	{/each}
</div>

<div class="cart-list">
	{#each cart as item }
		{#if item.quantity > 0}
		<div class="cart-item">
			<img width="50" src={item.image} alt={item.name}/>
			<div>{item.quantity}
				<button on:click={() => addItem(item)}>+</button> 
				<button on:click={() => removeItem(item)}>-</button>
			</div>
			<p>${item.price * item.quantity}</p>
		</div>
		{/if}
	{/each}
	<div class="total">
		<h4>Total: $ {total}</h4>
	</div>
</div>

<style>
/*styles go here*/
	main {
		text-align: center;
	}

	.product-list, .cart-item{
		display: grid;
		grid-template-columns: repeat(3, 1fr); /*specifies the line numbers and track sizing finction of the grids*/
	}

	.image{
		height: 150px; /*height of the content area*/
		width: 150px;  /*width of the content area*/
		background-size: contain;  /*specifies the size of background image*/
		background-position: center;
		background-repeat: no-repeat; /*specifies how background images are tiled*/
	}

	.total{
		text-align: right;
	}

	.cart-list{
		border: 2px solid; /*set the border*/
		padding: 10px;
	}
</style>