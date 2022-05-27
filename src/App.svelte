<script>
	import { faChevronDown , faChevronUp } from '@fortawesome/free-solid-svg-icons';

	import { FontAwesomeIcon, FontAwesomeLayers, FontAwesomeLayersText } from 'fontawesome-svelte';

	let arrays =[
		{
			id:1,
			title:"title1",
			description:"this is a description",
			open:false
		},
		{
			id:2,
			title:"title2",
			description:"this is a description",
			open:false
		},
		{
			id:3,
			title:"title3",
			description:"this is a description",
			open:false
		}
	]

	const handleClick =(id) =>{
		arrays = arrays.map(
			(item) => {
				if(item.id == id && !item.open) {
					item.open = true
				} else{
					item.open =false
				}
				return item
			}
		)
	}
</script>

<main>
	{#each arrays as item (item.id)}
		<div>
			<header>
				<h1> {item.title}</h1>
				<button on:click={()=>{handleClick(item.id)}} >
					{#if item.open}
						<FontAwesomeIcon icon={faChevronUp} />
					{:else}
						<FontAwesomeIcon icon={faChevronDown} />
					{/if}
				</button>
			</header>
			<div class="description">
				{#if item.open}
					<p>{item.description}</p>
				{/if}
			</div>
		</div>
	{:else}
	<p>There are item to show </p>
	{/each}
</main>

<style>
	main{
		margin: 20px auto;
		width:700px;
		font-family: Times, "Times New Roman", Georgia, serif;
	}
	header{
		display:flex;
		justify-content: space-between;
		align-items:center;
		background-color: #F8F9FA;
		padding: 20px;
		border-radius : 5px;
	}
	header h1{
		text-transform : capitalize
	}

	header button{
		border-radius:50%;
		background-color: transparent;
		border:none;
		cursor:pointer;
		transition: .3s all cubic-bezier(1, 0.25, 0.25, .8);	
	}
	.description p{
		margin : 20px 30px
	}
	
</style>