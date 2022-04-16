<script>
  import Papa from "papaparse";

  let files;
  let rows;
  $: {
    if (files) {
      Papa.parse(files[0], {
        header: true,
        dynamicTyping: true,
        complete: (results) => {
          console.log(results)
          rows = results.data.filter(row => row.qwe != null)
        },
      });
    }
  }
</script>

<input type="file" bind:files />
<br />
{#if rows && rows[0]}
<table>
  <tr>
    <th>qwe</th>
    <th>h1</th>
    <th>h2</th>
  </tr>
  {#each rows as row, i}
    <tr>
      <td>{row.qwe}</td>
      <td>{row.h1}</td>
      <td>{row.h2}</td>
    </tr>
  {/each}
</table>
{/if}
