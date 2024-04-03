<template>
	<div>
		<h2>input Value</h2>
		<!-- <input v-model.lazy="inputValue" type="text" /> -->
		<!-- <input v-model.number="inputValue" type="text" /> -->
		<input v-model.trim="inputValue" type="text" />
		<!-- :value="inputValue" -->
		<!-- @input="
				event => {
					inputValue = event.target.value;
				}
			" -->
		<div>{{ inputValue }}</div>
		<div>{{ typeof inputValue }}</div>
		<hr />
		<h2>textarea Value</h2>
		<textarea v-model="textareaValue"></textarea>
		<div>{{ textareaValue }}</div>
		<hr />
		<h2>checkbox value</h2>
		<label for="checkbox">{{ checkboxValue }}</label>
		<input
			type="checkbox"
			id="checkbox"
			v-model="checkboxValue"
			true-value="Yes"
			false-value="No"
		/>

		<hr />
		<h3>checkbox values</h3>
		<label>
			<input type="checkbox" value="html" v-model="checkboxValues" />
			html
		</label>
		<label>
			<input type="checkbox" value="css" v-model="checkboxValues" />
			css
		</label>
		<label>
			<input type="checkbox" value="javascript" v-model="checkboxValues" />
			javascript
		</label>
		<div>{{ checkboxValues }}</div>

		<hr />
		<label>
			<input type="radio" name="type" value="O" v-model="radioValue" />
			O형
		</label>
		<label>
			<input type="radio" name="type" value="A" v-model="radioValue" />
		</label>
		A형
		<div>{{ radioValue }}</div>
	</div>
	<hr />
	<div>selectbox Value</div>
	<select v-model="selectValue">
		<option value="html">HTML 수업</option>
		<option value="css">CSS 수업</option>
		<option value="javascript">JavaScript 수업</option>
	</select>
	<div>{{ selectValue }}</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const inputValue = ref(null);
		const textareaValue = ref(null);
		const checkboxValue = ref('Yes');
		const checkboxValues = ref([]);
		const selectValue = ref('html');
		const radioValue = ref('O');

		return {
			inputValue,
			textareaValue,
			checkboxValue,
			checkboxValues,
			radioValue,
			selectValue,
		};
	},
};
</script>

<style lang="scss" scoped></style>
