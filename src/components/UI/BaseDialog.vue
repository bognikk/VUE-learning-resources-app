<template>
	<teleport to="body">
		<div @click="$emit('closeDialog')"></div>
		<dialog open>
			<header>
				<slot name="header">
					<h2>{{ title }}</h2>
				</slot>
			</header>
			<section>
				<slot></slot>
			</section>
			<menu>
				<slot name="actions">
					<base-button @click="$emit('closeDialog')">Close</base-button>
				</slot>
			</menu>
		</dialog>
	</teleport>
</template>

<script>
export default {
	props: {
		title: {
			type: String,
			required: false,
		},
	},
	emits: ['closeDialog'],
};
</script>

<style lang="scss" scoped>
div {
	position: fixed;
	top: 0;
	left: 0;
	height: 100vh;
	width: 100%;
	background-color: rgba(0, 0, 0, 0.75);
	z-index: 10;
}

dialog {
	position: fixed;
	top: 20vh;
	left: 10%;
	width: 80%;
	z-index: 100;
	border-radius: 12px;
	border: none;
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
	padding: 0;
	margin: 0;
	overflow: hidden;

	@media (min-width: 768px) {
		left: calc(50% - 20rem);
		width: 40rem;
	}

	header {
		background-color: #3a0061;
		color: white;
		width: 100%;
		padding: 1rem;

		h2 {
			margin: 0;
		}
	}

	section {
		padding: 1rem;
	}

	menu {
		padding: 1rem;
		display: flex;
		justify-content: flex-end;
		margin: 0;
	}
}
</style>