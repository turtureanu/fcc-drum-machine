<script lang="ts">
	import { onMount } from 'svelte';

	const keys = ['Q', 'W', 'E', 'A', 'S', 'D', 'Z', 'X', 'C'];

	const keyNames = {
		Q: 'Heater 1',
		W: 'Heater 2',
		E: 'Heater 3',
		A: 'Heater 4',
		S: 'Clap',
		D: 'Open HH',
		Z: "Kick n' hat",
		X: 'Kick',
		C: 'Closed HH'
	};

	onMount(() => {
		addEventListener('keydown', (e) => {
			const key = e.key.toLocaleUpperCase();
			if (keys.includes(key)) {
				// @ts-expect-error
				document.getElementById(key).play();
				const pad = document.querySelector(`.drum-pad[data-key="${key}"]`);
				// @ts-expect-error
				pad.style.backgroundColor = '#803030';
				// @ts-expect-error
				setTimeout(() => (pad.style.backgroundColor = '#303040'), 100);
				// @ts-expect-error
				document.getElementById('display').innerHTML = keyNames[key];
			}
		});
	});

	const handleClick = (pad: string) => {
		// @ts-expect-error
		document.getElementById('display').innerHTML = keyNames[pad];

		// @ts-expect-error
		document.getElementById(pad).play();
	};
</script>

<div id="drum-machine">
	<div class="drum-pad-container">
		<button class="drum-pad" id="heater-1" data-key="Q" onclick={() => handleClick('Q')}>
			Q <audio
				src="https://cdn.freecodecamp.org/testable-projects-fcc/audio/Heater-1.mp3"
				class="clip"
				id="Q"
			></audio>
		</button>
		<button class="drum-pad" id="heater-2" data-key="W" onclick={() => handleClick('W')}>
			W <audio
				src="https://cdn.freecodecamp.org/testable-projects-fcc/audio/Heater-2.mp3"
				class="clip"
				id="W"
			></audio>
		</button>
		<button class="drum-pad" id="heater-3" data-key="E" onclick={() => handleClick('E')}>
			E <audio
				src="https://cdn.freecodecamp.org/testable-projects-fcc/audio/Heater-3.mp3"
				class="clip"
				id="E"
			></audio>
		</button>
		<button class="drum-pad" id="heater-4" data-key="A" onclick={() => handleClick('A')}>
			A <audio
				src="https://cdn.freecodecamp.org/testable-projects-fcc/audio/Heater-4_1.mp3"
				class="clip"
				id="A"
			></audio>
		</button>
		<button class="drum-pad" id="heater-6" data-key="S" onclick={() => handleClick('S')}>
			S <audio
				src="https://cdn.freecodecamp.org/testable-projects-fcc/audio/Heater-6.mp3"
				class="clip"
				id="S"
			></audio>
		</button>
		<button class="drum-pad" id="dsc-oh" data-key="D" onclick={() => handleClick('D')}>
			D <audio
				src="https://cdn.freecodecamp.org/testable-projects-fcc/audio/Dsc_Oh.mp3"
				class="clip"
				id="D"
			></audio>
		</button>
		<button class="drum-pad" id="kick-n-hat" data-key="Z" onclick={() => handleClick('Z')}>
			Z <audio
				src="https://cdn.freecodecamp.org/testable-projects-fcc/audio/Kick_n_Hat.mp3"
				class="clip"
				id="Z"
			></audio>
		</button>
		<button class="drum-pad" id="rp4-kick-1" data-key="X" onclick={() => handleClick('X')}>
			X <audio
				src="https://cdn.freecodecamp.org/testable-projects-fcc/audio/RP4_KICK_1.mp3"
				class="clip"
				id="X"
			></audio>
		</button>
		<button class="drum-pad" id="cev-h2" data-key="C" onclick={() => handleClick('C')}>
			C <audio
				src="https://cdn.freecodecamp.org/testable-projects-fcc/audio/Cev_H2.mp3"
				class="clip"
				id="C"
			></audio>
		</button>
	</div>
	<div id="display">Play using your keyboard!</div>
</div>

<style>
	#drum-machine {
		height: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
	}

	#display {
		margin-top: 1em;
		font-size: 2rem;
		text-align: center;
	}

	button {
		border: none;
		font-size: 1rem;
		color: white;
		font-weight: 900;
		cursor: pointer;
	}

	button:hover {
		background-color: #303060 !important;
	}

	button:active {
		background-color: #803030 !important;
	}

	.drum-pad-container {
		display: grid;
		width: 50vw;
		height: 50vw;
		grid-template-columns: repeat(3, 1fr);
	}

	.drum-pad {
		padding: 1em;
		background-color: #303040;
		margin: 0;
		display: block;
	}
</style>
