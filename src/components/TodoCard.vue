<template>
    <div
        :id="id"
        class="card"
        :draggable="draggable"
        @dragstart="dragStart"
    >
        <slot />
    </div>
</template>

<script>
export default {
    props: ['id', 'draggable'],
    methods: {
        dragStart(e) {
            // Drag starts, 
            const target = e.target;
            // Get the dragging card id
            e.dataTransfer.setData('card_id', target.id);
        },
        dragEnd(e) {
            // Drag ends, clear data
            e.dataTransfer.clearData();
        }
    }
}
</script>