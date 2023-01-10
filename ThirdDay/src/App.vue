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
	},
	methods: {
		checkStudentOnSearch(fullName) {
			if (this.searchTerm === '') return

			const loweredFullName = fullName.toLowerCase()
			const loweredSearchTerm = this.searchTerm.toLowerCase()

			return loweredFullName.indexOf(loweredSearchTerm) >= 0
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
			</tr>
			<!-- WARNING: key as fullName? -->
			<tr
				v-for="student in students"
				:key="student.fullName"
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
