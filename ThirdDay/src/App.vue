<script>
export default {
	data() {
		return {
			searchTerm: '',
			students: [
				{
					id: 0,
					fullName: 'John Smith',
					group: 'A',
					yearOfBirth: 2000,
					passed: true
				},
				{
					id: 1,
					fullName: 'Zack Philips',
					group: 'B',
					yearOfBirth: 2001,
					passed: false
				},
				{
					id: 2,
					fullName: 'Jack Johnson',
					group: 'C',
					yearOfBirth: 2002,
					passed: true
				}
			]
		}
	},
	methods: {
		checkStudentOnSearch(fullName) {
			if (this.searchTerm === '') return

			const loweredFullName = fullName.toLowerCase()
			const loweredSearchTerm = this.searchTerm.toLowerCase()

			return loweredFullName.indexOf(loweredSearchTerm) >= 0
		},
		deleteStudent(id) {
			const index = this.students.findIndex(student => student.id === id)
			this.students.splice(index, 1)
		}
	}
}
</script>

<template>
	<div>
		<label>
			Search:
			<input
				type="text"
				v-model="searchTerm"
			/>
		</label>

		<table>
			<tr>
				<th>Full Name</th>
				<th>Group</th>
				<th>Year of Birth</th>
				<th>Passed Practical Work</th>
				<th>Button Delete</th>
			</tr>

			<tr
				v-for="student in students"
				:key="student.id"
				:class="checkStudentOnSearch(student.fullName) && 'studentHighlight'"
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
				<td>
					<button v-on:click="deleteStudent(student.id)">Delete</button>
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

.studentHighlight {
	color: red;
}
</style>
