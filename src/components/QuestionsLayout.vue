<template>
	<div class="question-container">
		<div v-for="question in questionArray" :key="question.id">
			<div class="question-title">
				<h2
					class="animate__animated animate__bounceInLeft"
					v-if="question.id == count"
				>
					{{ question.questionStatement }}
				</h2>
			</div>
			<div
				class="answer-box animate__animated animate__bounceInLeft"
				v-if="question.id == count"
			>
				<button class="btn" @click.prevent="handleClick">
					{{ question.answers.a }}
				</button>
				<button class="btn" @click.prevent="handleClick">
					{{ question.answers.b }}
				</button>
				<button class="btn" @click.prevent="handleClick">
					{{ question.answers.c }}
				</button>
				<button class="btn" @click.prevent="handleClick">
					{{ question.answers.d }}
				</button>
			</div>
		</div>
		<div class="next" v-if="count == 6 ? !isDisabled : isDisabled">
			<button @click="next" v-show="!isDisabled">Next</button>
		</div>
		<!-- result div can be a different component -->
		<div class="result animate__animated animate__bounceInUp" v-else>
			<h1>Result</h1>
			<span
				>Your Score: <b>{{ scoreData }}</b></span
			>
			<p v-if="scoreData <= 3">Oops.. Try Harder Next Time!</p>
			<p v-else>Woah.. That is Impressive!</p>
			<button class="reset" @click="reset">Reset</button>
		</div>
	</div>
</template>

<script>
export default {
	name: "QuestionsLayout",
	props: ["scoreData"],
	data() {
		return {
			isDisabled: true,
			count: 1,
			score: 1,

			questionArray: [
				{
					id: 1,
					questionStatement: "Which two countries share the longest border?",
					answers: {
						a: "USA & Canada",
						b: "Russia & China",
						c: "Norway & Sweden",
						d: "Brazil & Chile",
					},
					correctAnswer: "USA & Canada",
				},
				{
					id: 2,
					questionStatement: "What is the square root of 256?",
					answers: {
						a: "12",
						b: "18",
						c: "14",
						d: "16",
					},
					correctAnswer: "16",
				},
				{
					id: 3,
					questionStatement: "What is the full form of ICICI?",
					answers: {
						a: "Industrial Corporation and Credit Investment of India",
						b: "Industrial Credit and Investment Corporation of India",
						c: "Investment Credit and Industrial Corporation of India",
						d: "Investment Corporation and Industrial Credit of India",
					},
					correctAnswer:
						"Industrial Credit and Investment Corporation of India",
				},
				{
					id: 4,
					questionStatement: "What is the full form of SIM?",
					answers: {
						a: "Service Identification Module",
						b: "Subscriber Identity Memory",
						c: "Subscriber Identity Module",
						d: "Service Identification Memory",
					},
					correctAnswer: "Subscriber Identity Module",
				},
				{
					id: 5,
					questionStatement: "What was the first animal to go into orbit?",
					answers: {
						a: "Rabbit",
						b: "Dog",
						c: "Monkey",
						d: "Cat",
					},
					correctAnswer: "Dog",
				},
			],
		};
	},
	methods: {
		next() {
			this.count++;
			document.querySelector(".next button").style.display = "none";
		},
		handleClick(e) {
			if ("USA & Canada" == e.target.textContent) {
				this.$emit("scoreUpdate", this.score++);
				e.target.style.backgroundColor = "#41B883";
				e.target.style.color = "#FFFFFF";
				document.querySelectorAll(".btn").forEach((elem) => {
					elem.disabled = true;
				});
				document.querySelector(".next button").style.display = "unset";
			} else if ("16" == e.target.textContent) {
				this.$emit("scoreUpdate", this.score++);
				e.target.style.backgroundColor = "#41B883";
				e.target.style.color = "#FFFFFF";
				document.querySelectorAll(".btn").forEach((elem) => {
					elem.disabled = true;
				});
				document.querySelector(".next button").style.display = "unset";
			} else if (
				"Industrial Credit and Investment Corporation of India" ==
				e.target.textContent
			) {
				this.$emit("scoreUpdate", this.score++);
				e.target.style.backgroundColor = "#41B883";
				e.target.style.color = "#FFFFFF";
				document.querySelectorAll(".btn").forEach((elem) => {
					elem.disabled = true;
				});
				document.querySelector(".next button").style.display = "unset";
			} else if ("Subscriber Identity Module" == e.target.textContent) {
				this.$emit("scoreUpdate", this.score++);
				e.target.style.backgroundColor = "#41B883";
				e.target.style.color = "#FFFFFF";
				document.querySelectorAll(".btn").forEach((elem) => {
					elem.disabled = true;
				});
				document.querySelector(".next button").style.display = "unset";
			} else if ("Dog" == e.target.textContent) {
				this.$emit("scoreUpdate", this.score++);
				e.target.style.backgroundColor = "#41B883";
				e.target.style.color = "#FFFFFF";
				document.querySelectorAll(".btn").forEach((elem) => {
					elem.disabled = true;
				});
				document.querySelector(".next button").style.display = "unset";
			} else {
				// alert("Sorry wrong answer, move to next question!");
				e.target.style.backgroundColor = "#FF0000";
				e.target.style.color = "#FFFFFF";
				document.querySelectorAll(".btn").forEach((elem) => {
					elem.disabled = true;
					if (elem.textContent == "USA & Canada") {
						elem.style.backgroundColor = "#41B883";
						elem.style.color = "#FFFFFF";
					} else if (elem.textContent == "16") {
						elem.style.backgroundColor = "#41B883";
						elem.style.color = "#FFFFFF";
					} else if (
						elem.textContent ==
						"Industrial Credit and Investment Corporation of India"
					) {
						elem.style.backgroundColor = "#41B883";
						elem.style.color = "#FFFFFF";
					} else if (elem.textContent == "Subscriber Identity Module") {
						elem.style.backgroundColor = "#41B883";
						elem.style.color = "#FFFFFF";
					} else if (elem.textContent == "Dog") {
						elem.style.backgroundColor = "#41B883";
						elem.style.color = "#FFFFFF";
					}
				});
				document.querySelector(".next button").style.display = "unset";
			}
		},
		reset() {
			location.reload();
		},
	},
};
</script>

<style>
.question-container {
	display: grid;
	/* border: 1px solid #eee;
    box-shadow: 0px 0px 10px #e1e1e1; */
	padding: 10px;
	width: 100%;
	max-width: 70%;
	margin: 20px auto;
}
.answer-box {
	display: grid;
	grid-template-columns: auto auto;
	grid-row-gap: 10px;
	margin: 10px auto;
	grid-row-gap: 1rem;
	grid-column-gap: 4rem;
	justify-content: center;
}

.answer-box button {
	background: transparent;
	border: 1px solid #eee;
	box-shadow: 5px 5px 10px #e1e1e1;
	padding: 10px;
	width: 250px;
	cursor: pointer;
	outline: none;
}

.next button,
.reset {
	background-color: teal;
	border: 1px solid teal;
	box-shadow: 5px 5px 10px #b1b1b1;
	padding: 10px;
	width: 200px;
	cursor: pointer;
	margin: 20px auto;
	color: #fff;
	outline: none;
}

@media screen and (max-width: 668px) {
	.question-container {
		display: block;
		border: none;
		box-shadow: none;
		padding: 10px;
		width: unset;
		max-width: none;
		margin: none;
	}

	.answer-box {
		width: fit-content;
		grid-template-columns: unset;
	}
}
</style>
