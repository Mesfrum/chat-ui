<script>
	let novelType = "";
	let description = "";
	let writtenClauses = "";
	let shortMemory = "";
	let longMemory = "";
	let instructions = ["", "", ""];
	let selectedPlan = "";
	let selectedInstruction = "";
    import HumanLoop from "./HumanLoop.svelte";

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
</script>

<div class="container mt-12 flex flex-col px-1">
	<div class="flex border-b border-gray-200">
		<button
			class="px-4 py-2 text-gray-400 focus:text-gray-200 focus:outline-none hover:text-gray-300"
			class:active={activeTab === 0}
			on:click={() => switchTab(0)}>Auto Generation</button
		>
		<button
			class="px-4 py-2 text-gray-400 focus:text-gray-200 focus:outline-none hover:text-gray-300"
			class:active={activeTab === 1}
			on:click={() => switchTab(1)}>Human-in-loop</button
		>
	</div>

	<div class="scrollbar-custom m-2 mt-4" style="height: 600px; overflow-y: auto;">
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
						<div>
							<label for="">Revised Instruction (from last step)</label>
							<textarea
								class="mt-2 w-full rounded-md border p-2"
								bind:value={selectedPlan}
								rows="1"
								placeholder="Revised Instruction (from last step)"
							/>
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

		<div class={activeTab === 1 ? "block" : "hidden"}>
			<!-- Content for Human-in-loop -->
			<!-- <p class="text-gray-700">This is Human-in-loop content.</p> -->
            <HumanLoop></HumanLoop>
		</div>
	</div>
</div>
