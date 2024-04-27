<script>
  import {
    importData,
    exportData,
    importCountriesData,
    exportCountriesData,
    customsData,
  } from "$lib/data.js";

  let openDropdown = false;
  let tableType = 0;
  let tableText = "Top countries by import";

  const changeTable = (e) => {
    tableType = e.target.getAttribute("id");
    tableText = e.target.innerText;
    openDropdown = false;
  };
</script>

<div class="table-container">
  <div class="drop-down">
    <div
      class="selected"
      on:click={() => (openDropdown = !openDropdown)}
      style={openDropdown
        ? "border-bottom-right-radius: 0; border-bottom-left-radius: 0; border-bottom: 2px solid #797979;"
        : ""}
    >
      <span class="selected-txt">{tableText}</span>
      <i class={openDropdown ? 'fa-solid fa-chevron-up arrow' : 'fa-solid fa-chevron-down arrow'}></i>
    </div>
    {#if openDropdown}
      <div class="options" on:click={changeTable}>
        <li id="0">Top countries by import</li>
        <li id="1">Top countries by export</li>
        <li id="2">Top import by commodity</li>
        <li id="3">Top export by commodity</li>
        <li id="4">Import and export by custom offices</li>
      </div>
    {/if}
  </div>

  <div class="table-container">
    {#if tableType == 0}
      <table>
        <thead>
          <tr>
            <td>S.N</td>
            <td>Country</td>
            <td>Import</td>
            <td>Export</td>
            <td>Balance</td>
          </tr>
        </thead>
        <tbody>
          {#each importCountriesData as data, i}
            <tr>
              <td class="sn-td">{i + 1}</td>
              <td class="desc-td">{data.country}</td>
              <td>{data.import}</td>
              <td class="right-td">{data.export}</td>
              <td class="right-td">{data.balance}</td>
            </tr>
          {/each}
        </tbody>
      </table>
    {:else if tableType == 1}
      <table>
        <thead>
          <tr>
            <td>S.N</td>
            <td>Country</td>
            <td>Import</td>
            <td>Export</td>
            <td>Balance</td>
          </tr>
        </thead>
        <tbody>
          {#each exportCountriesData as data, i}
            <tr>
              <td class="sn-td">{i + 1}</td>
              <td class="desc-td">{data.country}</td>
              <td>{data.import}</td>
              <td class="right-td">{data.export}</td>
              <td class="right-td">{data.balance}</td>
            </tr>
          {/each}
        </tbody>
      </table>
    {:else if tableType == 2}
      <table>
        <thead>
          <tr>
            <td>S.N</td>
            <td>Description</td>
            <td>Unit</td>
            <td>Quantity</td>
            <td>Import value</td>
            <td>Revenue</td>
          </tr>
        </thead>
        <tbody>
          {#each importData as data, i}
            <tr>
              <td class="sn-td">{i + 1}</td>
              <td class="desc-td">{data.description}</td>
              <td>{data.unit}</td>
              <td class="right-td">{data.quantity}</td>
              <td class="right-td">{data.import_value}</td>
              <td class="right-td">{data.import_revenue}</td>
            </tr>
          {/each}
        </tbody>
      </table>
    {:else if tableType == 3}
      <table>
        <thead>
          <tr>
            <td>S.N</td>
            <td>Description</td>
            <td>Unit</td>
            <td>Quantity</td>
            <td>Export value</td>
          </tr>
        </thead>
        <tbody>
          {#each exportData as data, i}
            <tr>
              <td class="sn-td">{i + 1}</td>
              <td class="desc-td">{data.description}</td>
              <td>{data.unit}</td>
              <td class="right-td">{data.quantity}</td>
              <td class="right-td">{data.export_value}</td>
            </tr>
          {/each}
        </tbody>
      </table>
    {:else if tableType == 4}
      <table>
        <thead>
          <tr>
            <td>S.N</td>
            <td>Custom</td>
            <td>Import</td>
            <td>Import share</td>
            <td>Export</td>
            <td>Export share</td>
          </tr>
        </thead>
        <tbody>
          {#each customsData as data, i}
            <tr>
              <td class="sn-td">{i + 1}</td>
              <td class="desc-td">{data.custom}</td>
              <td>{data.import}</td>
              <td class="right-td">{data.import_share.toFixed(2)}</td>
              <td class="right-td">{data.export}</td>
              <td class="right-td">{data.export_share.toFixed(2)}</td>
            </tr>
          {/each}
        </tbody>
      </table>
    {/if}
  </div>
</div>

<style>
  .table-container {
    width: 100%;
    flex-direction: column;
  }
  .drop-down {
    margin-bottom: 1rem;
    width: 350px;
  }
  .selected {
    padding: 0.5rem 1rem;
    width: 100%;
    font-size: 1.25rem;
    font-weight: bold;
    text-align: center;
    color: #fff;
    background-color: var(--blue);
    border-radius: 3px;
    cursor: pointer;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .selected-txt {
    max-width: 300px;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
  }
  .options li:last-child {
    border-bottom-left-radius: 3px;
    border-bottom-right-radius: 3px;
  }
  .options li {
    padding: 0.25rem 1rem;
    width: 100%;
    border: 1px solid var(--blue);
  }
  .options li:hover {
    color: #fff;
    background-color: var(--blue);
    transition: 0.3s;
    cursor: pointer;
  }

  table {
    width: 100%;
    background-color: #fff;
    border: 2px solid #797979;
    border-collapse: collapse;
  }
  thead td {
    padding: 0.75rem 0.5rem;
    font-weight: bold;
    background-color: var(--green);
    color: #fff;
  }
  td {
    padding: 0.5rem;
    border: 1px solid var(--blue);
    border: 1px solid #797979;
  }
  .sn-td {
    text-align: center;
  }
  .desc-td {
    width: 400px;
    line-height: 1.2rem;
  }
  .right-td {
    text-align: right;
  }
</style>
