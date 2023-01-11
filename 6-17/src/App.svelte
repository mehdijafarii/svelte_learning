<script>
  import Modal from "./Modal.svelte";
  import AddPersonForm from "./AddPersonForm.svelte";

  let people = [
    { name: "Rana", age: 31, beltColor: "Black", id: 1 },
    { name: "Mahdi", age: 25, beltColor: "White", id: 2 },
    { name: "Hossein", age: 35, beltColor: "Orange", id: 3 },
  ];

  const removePeople = (id) => {
    people = people.filter((p) => {
      return p.id != id;
    });
  };

  const toggleModal = () => {
    return (showModel = !showModel);
  };

  const newPerson = (e) => {
    const person = e.detail;
    people = [person, ...people];
    showModel = false;
    console.log("The person:");
    console.log(person);
    console.log("The people:");
    console.log(people);
  };

  let showModel = false;

  // let num = 5;
</script>

<!-- {#if num > 20}
  <p>Number is bigger than 20</p>
{:else if num > 5}
  <p>Number is bigger than 5 less than 20</p>
{:else}
  <p>Less than 5</p>
{/if} -->

<Modal {showModel} on:click={toggleModal}>
  <AddPersonForm on:addPersonDispatch={newPerson} />
</Modal>

<main>
  <button on:click={toggleModal}>Add New Person</button>
  {#each people as person (person.id)}
    <div>
      <h4>{person.name}</h4>
      {#if person.beltColor === "Black"}
        <p><strong>Master Ninja</strong></p>
      {/if}
      <p>{person.age} years old! with {person.beltColor}.</p>
      <button
        on:click={() => {
          removePeople(person.id);
        }}>Delete</button
      >
    </div>
  {:else}
    <p>No people to shows</p>
  {/each}
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
