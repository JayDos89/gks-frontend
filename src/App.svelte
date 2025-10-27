<script>
  // Sample data — in a real app, this might come from a backend API.

  //import NavBar from "../NavBar.svelte";

  let scores = [
    { name: 'Alice', score: 1200 },
    { name: 'Bob', score: 950 },
    { name: 'Charlie', score: 700 }
  ];

  let newName = '';
  let newScore = '';

  function addScore() {
    if (!newName || !newScore) return;
    scores = [...scores, { name: newName, score: parseInt(newScore) }];
    scores.sort((a, b) => b.score - a.score); // sort descending
    newName = '';
    newScore = '';
  }
</script>

<div class="">

    <h1>🏆 High Scores</h1>

    <table>
      <thead>
        <tr>
          <th>Rank</th>
          <th>Name</th>
          <th>Score</th>
        </tr>
      </thead>
      <tbody>
        {#each scores as { name, score }, i}
          <tr>
            <td>{i + 1}</td>
            <td>{name}</td>
            <td>{score}</td>
          </tr>
        {/each}
      </tbody>
    </table>

    <form on:submit|preventDefault={addScore}>
      <input
        type="text"
        placeholder="Name"
        bind:value={newName}
      />
      <input
        type="number"
        placeholder="Score"
        bind:value={newScore}
      />
      <button type="submit">Add Score</button>
    </form>

</div>

<style>

  h1 {
    text-align: center;
    margin-top: 1rem;
  }

  table {
    margin: 1rem auto;
    border-collapse: collapse;
    width: 60%;
  }

  th, td {
    border: 1px solid #ddd;
    padding: 0.75rem;
    text-align: center;
  }

  th {
    background-color: #f0f0f0;
  }

  form {
    display: flex;
    justify-content: center;
    gap: 1rem;
    margin: 2rem;
  }

  input {
    padding: 0.5rem;
    font-size: 1rem;
  }

  button {
    padding: 0.5rem 1rem;
    cursor: pointer;
  }
</style>
