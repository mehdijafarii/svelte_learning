<script>
  import { createEventDispatcher } from "svelte";

  let dispach = createEventDispatcher();

  let name;
  let beltColor;
  let age;

  // This is the indiviual value binded as shown
  // let fighting = false;
  // let running = false;
  // let skying = false;

  let skills = [];

  const handleSubmit = () => {
    console.log(age, beltColor, name, skills);

    const person = {
      name,
      beltColor,
      age,
      skills,
      id: Math.random(),
    };

    dispach("addPersonDispatch", person);
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
  <input type="text" placeholder="name" bind:value={name} />
  <input type="number" placeholder="age" bind:value={age} />
  <!-- svelte-ignore a11y-label-has-associated-control -->
  <label>Skills:</label>
  <!-- <input type="checkbox" bind:checked={fighting} /> Fighting <br />
  <input type="checkbox" bind:checked={running} /> Running <br />
  <input type="checkbox" bind:checked={skying} /> Skying <br /> -->
  <input type="checkbox" bind:group={skills} value="fighting" /> Fighting <br />
  <input type="checkbox" bind:group={skills} value="running" /> Running <br />
  <input type="checkbox" bind:group={skills} value="skying" /> Skying <br />

  <!-- svelte-ignore a11y-label-has-associated-control -->
  <label>Belt Colour:</label>
  <select bind:value={beltColor}>
    <option value="black">black</option>
    <option value="orange">orange</option>
    <option value="white">white</option>
  </select>

  <button>Add Person</button>
</form>

<style>
</style>
