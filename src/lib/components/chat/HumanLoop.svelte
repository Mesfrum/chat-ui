<script>
	let novelType = "";
	let description = "";
	let writtenClauses = "";
	let shortMemory = "";
	let longMemory = "";
	let instructions = ["", "", ""];
	let selectedPlan = "";
	let selectedInstruction = "";

	const initDocumentGeneration = () => {
		// Logic for initializing document generation
	};

	const nextStep = () => {
		// Logic for moving to the next step
	};

	let activeTab = 0;

	function switchTab(index) {
		activeTab = index;
	}

	const handleRadioChange = (event) => {
		selectedPlan = event.target.value;
	};

	const handleTextboxChange = (event) => {
		selectedInstruction = event.target.value;
	};

	const instructionsRadio = ["Instruction 1", "Instruction 2", "Instruction 3"];
</script>

<div>
	<div class={activeTab === 0 ? "block" : "hidden"}>
		<!-- Content for Auto Generation -->
		<div class="grid grid-cols-2 gap-4">
			<!-- Left column -->
			<div class="flex flex-col space-y-2">
				<div class="flex flex-row space-x-4">
					<div class="flex w-1/2 flex-col">
						<label for="documentType" class="text-sm font-semibold">Document Type</label>
						<textarea
							id="documentType"
							class="w-full rounded-md border p-2"
							rows="1"
							bind:value={novelType}
							placeholder="Document Type"
						/>
					</div>
					<div class="flex w-1/2 flex-col">
						<label for="description" class="text-sm font-semibold">Description</label>
						<textarea
							id="description"
							class="w-full rounded-md border p-2"
							rows="1"
							bind:value={description}
							placeholder="Description"
						/>
					</div>
				</div>
				<div class="flex w-full flex-col justify-center gap-4">
					<div>
						<button
							class="mt-4 w-full rounded-md bg-amber-700 px-4 py-2 text-white"
							on:click={initDocumentGeneration}>Init Document Generation</button
						>
					</div>
					<div>
						<label for="">Written Clauses (editable)</label>
						<textarea
							class="mt-4 w-full rounded-md border p-2"
							bind:value={writtenClauses}
							rows="10"
							placeholder="Written Clauses (editable)"
						/>
					</div>
				</div>
			</div>

			<!-- Right column -->
			<div class="flex flex-col">
				<!-- Add content for the right column -->
				<div class="flex flex-col">
					<h4 class="text-lg font-semibold">Memory Module</h4>
					<div class="flex flex-col gap-4 rounded-md p-1">
						<div class="flex flex-col">
							<label for="">Short-Term Memory (editable)</label>
							<input
								type="text"
								class="mt-2 rounded-md border p-2"
								bind:value={shortMemory}
								placeholder="Short-Term Memory (editable)"
							/>
						</div>
						<div class="flex flex-col">
							<label for="">Long-Term Memory (editable)</label>
							<textarea
								class="mt-2 rounded-md border p-2"
								bind:value={longMemory}
								rows="4"
								placeholder="Long-Term Memory (editable)"
							/>
						</div>
					</div>
				</div>
				<div class="flex flex-col space-y-2">
					<h4 class="mt-2 text-lg font-semibold">Instruction Module</h4>
					<div class="flex">
						{#each instructions as instruction, index}
							<div class="flex w-1/3 flex-col">
								<label for="">{`Instruction ${index + 1}`}</label>
								<textarea
									class="mr-2 mt-2 flex-1 rounded-md border p-2"
									bind:value={instructions[index]}
									rows="2"
									placeholder={`Instruction ${index + 1}`}
								/>
							</div>
						{/each}
					</div>
					<div class="flex items-start space-x-2">
						<!-- Left column for radio buttons -->
						<div class="flex w-1/3 flex-col justify-center">
							<h2 class="mb-2">Instruction Selection:</h2>
							{#each instructionsRadio as instruction}
								<div class="mb-2 flex items-center ml-1">
									<input
										type="radio"
										id={instruction}
										name="instruction"
										value={instruction}
										class="form-radio h-4 w-4 rounded border border-gray-300 text-indigo-600 focus:ring-indigo-500"
										bind:group={selectedPlan}
										on:change={handleRadioChange}
									/>
									<label for={instruction} class="ml-2">{instruction}</label>
								</div>
							{/each}
						</div>

						<!-- Right column for textarea -->
						<div class="flex w-2/3 flex-col">
							<label for="" class="mb-2">Revised Instruction (from last step)</label>
							<textarea
								class="w-full rounded-md border p-2"
								bind:value={selectedPlan}
								rows="2"
								placeholder="Revised Instruction (from last step)"
							/>
						</div>
					</div>
				</div>
				<div>
					<button
						class="mt-4 w-full rounded-md bg-amber-700 px-4 py-2 text-white"
						on:click={nextStep}
						>Next step
					</button>
				</div>
			</div>
		</div>
	</div>
</div>

<style>
	/* Default styles for form-radio */
	.form-radio {
		appearance: none;
		-webkit-appearance: none;
		-moz-appearance: none;
		display: inline-block;
		vertical-align: middle;
		background-origin: border-box;
		user-select: none;
		flex-shrink: 0;
		height: 1.2em;
		width: 1.2em;
		color: #1a202c;
		background-color: #fff;
		border-color: #d2d6dc;
		border-width: 1px;
		border-radius: 0.25rem;
		transition: background-color 150ms ease-in-out, border-color 150ms ease-in-out;
	}

	.form-radio:checked {
		background-color: #3b76ed;
		border-color: #ffffff;
	}
</style>
