<div class="input-group">
	<input 
		type="text" 
		class="form-control" 
		placeholder="Remember the milk" 
		bind:value={todoInput}
		on:keypress={addWithReturn}
	/>
	<button 
		class="btn btn-outline-success"
		on:click={addItem}
	>
		{buttonLabel}
	</button>
</div>

<script>
	import { createEventDispatcher } from 'svelte'

	export let buttonLabel
	const dispatch = createEventDispatcher()
	let todoInput = null

	function addItem () {
		dispatch('addItem', {
			value: todoInput
		})
		todoInput = null
	}

	function addWithReturn (event) {
		if (event.charCode === 13) addItem()
	}
</script>