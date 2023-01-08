<script>
  let people = [
    { name: "Rana", age: 31, beltColor: "Black", id: 1 },
    { name: "Mahdi", age: 25, beltColor: "White", id: 2 },
    { name: "Hossein", age: 35, beltColor: "Orange", id: 3 },
  ];

  const removePeople = (id)=>{
    people = people.filter((p) => {
      return p.id != id;
    })
  }
</script>

<main>
  {#each people as person (person.id)}
    <div>
      <h4>{person.name}</h4>
      <p>{person.age} years old! with {person.beltColor}.</p>
      <button on:click={()=> {removePeople(person.id)}}>Delete</button>
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
