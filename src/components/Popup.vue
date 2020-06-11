<template>
	<div class="text-center">
		<v-dialog v-model="dialog" width="500">
			<template v-slot:activator="{ on }">
				<v-btn class="success" dark v-on="on">Add New Project</v-btn>
			</template>
			<v-card>
				<v-card-title class="headline grey lighten-2" primary-title
					>Add a New Project</v-card-title
				>

				<v-card-text>
					<v-form class="px-3" ref="form">
						<v-text-field
							:rules="inputRules"
							label="Title"
							v-model="title"
							prepend-icon="mdi-folder"
						></v-text-field>
						<v-textarea
							:rules="inputRules"
							label="Information"
							v-model="content"
							prepend-icon="mdi-pen"
						></v-textarea>
						<v-menu max-width="290">
							<template v-slot:activator="{ on }">
								<v-text-field
									:rules="inputRules"
									:value="formattedDate"
									label="Due date"
									prepend-icon="mdi-calendar-range"
									v-on="on"
								></v-text-field>
							</template>

							<v-date-picker v-model="due"></v-date-picker>
						</v-menu>
						<v-btn text class="success mx-0 mt-3" @click="submit"
							>Add Project</v-btn
						>
					</v-form>
				</v-card-text>
			</v-card>
		</v-dialog>
	</div>
</template>

<script>
import moment from 'moment';

export default {
	computed: {
		formattedDate() {
			return this.due ? moment(this.due).format('Do MMMM YYYY') : '';
		},
	},
	data() {
		return {
			title: '',
			content: '',
			dialog: false,
			due: null,
			inputRules: [
				(v) => (v && v.length >= 3) || 'Minimum length is 3 characters',
			],
		};
	},
	methods: {
		submit() {
			if (this.$refs.form.validate()) console.log(this.title, this.content);
		},
	},
};
</script>

<style></style>
