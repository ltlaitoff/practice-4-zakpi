<script>
export default {
	data() {
		return {
			searchTerm: '',
			students: [
				{
					fullName: 'John Smith',
					group: 'A',
					yearOfBirth: 2000,
					passed: true
				},
				{
					fullName: 'Jane Doe',
					group: 'B',
					yearOfBirth: 2001,
					passed: false
				},
				{
					fullName: 'Jack Johnson',
					group: 'C',
					yearOfBirth: 2002,
					passed: true
				}
			]
		}
	}
}
// const studentsArr = [
// 	{
// 		id: 0,
// 		name: 'Jaleel',
// 		surname: 'Medhurst',
// 		practiceWork: true
// 	},
// 	{
// 		id: 1,
// 		name: 'Ida',
// 		surname: 'Addison',
// 		practiceWork: false
// 	},
// 	{
// 		id: 2,
// 		name: 'Hipolito',
// 		surname: 'Dexter',
// 		practiceWork: true
// 	},
// 	{
// 		id: 3,
// 		name: 'Myah',
// 		surname: 'Sally',
// 		practiceWork: false
// 	},
// 	{
// 		id: 4,
// 		name: 'Helen',
// 		surname: 'Bethany',
// 		patronymic: 'Isom',
// 		group: '2',
// 		dateOfBirthday: '07/02/2002',
// 		practiceWork: true
// 	},
// 	{
// 		id: 5,
// 		name: 'Luisa',
// 		surname: 'Amalia',
// 		practiceWork: false
// 	},
// 	{
// 		id: 6,
// 		name: 'Donnell',
// 		surname: 'Davin',
// 		practiceWork: false
// 	}
// ]
// const students = reactive(studentsArr)
// const filter = ref('')
</script>

<template>
	<!-- <input
		type="text"
		v-model="filter"
	/>

	<table class="table">
		<tr class="tableHead">
			<th class="tableHeadItem">FullName</th>
			<th class="tableHeadItem">PracticeWork</th>
		</tr>
		<tr
			class="tableContent"
			v-for="student in students"
			:key="student.id"
		>
			<td
				:class="[
					'tableContentItem',
					filter !== '' &&
						`${student.surname} ${student.name} `.indexOf(filter) >= 0 &&
						'tableContentItemColor'
				]"
			>
				{{ `${student.surname} ${student.name} ` }}
			</td>
			<td class="tableContentItem">
				<input
					type="checkbox"
					v-model="student.practiceWork"
				/>
			</td>

			<button @click="deleteItem(student.id)">Delete</button>
		</tr>
	</table> -->
	<div>
		<input
			type="text"
			v-model="searchTerm"
		/>
		<table>
			<tr>
				<th>Full Name</th>
				<th>Group</th>
				<th>Year of Birth</th>
				<th>Passed Practical Work</th>
			</tr>
			<tr
				v-for="student in students"
				:key="student.fullName"
				v-if="student.fullName.includes(searchTerm)"
			>
				<td>{{ student.fullName }}</td>
				<td>{{ student.group }}</td>
				<td>{{ student.yearOfBirth }}</td>
				<td>
					<input
						type="checkbox"
						v-model="student.passed"
					/>
				</td>
			</tr>
		</table>
	</div>
</template>

<style scoped>
header {
	line-height: 1.5;
}

.logo {
	display: block;
	margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
	header {
		display: flex;
		place-items: center;
		padding-right: calc(var(--section-gap) / 2);
	}

	.logo {
		margin: 0 2rem 0 0;
	}

	header .wrapper {
		display: flex;
		place-items: flex-start;
		flex-wrap: wrap;
	}
}
</style>
