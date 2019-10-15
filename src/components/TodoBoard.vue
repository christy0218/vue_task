<template>
	<div
		:id="id"
		class="board"
		@dragover.prevent
		@drop.prevent="drop"
	>
		<slot />
	</div>
</template>

<script>
export default {
	props: ['id', 'all'],
	methods: {
		drop(e) {
			// Get the dragging card and place it
			const card_id = e.dataTransfer.getData('card_id');

			// Get the board id where the card has dropped
			const board_id = e.target.id;

			// Prevent dropping onto areas other than the boards
			if (board_id == 'to_do' || board_id == 'in_progress' || board_id == 'done') {
				this.all[card_id].progress = board_id;
			} 
			else if (!board_id){
				// When it is  dropped onto the card item
				if (e.target.offsetParent.id) {
						const parent_board_id = e.target.offsetParent.id;
						this.all[card_id].progress = parent_board_id;
				}
			}
		}
	}
}
</script>