<script>
<<<<<<< HEAD
  import { onMount } from "svelte";
  import { createEventDispatcher } from "svelte";

  let jsonData = [];
  let tableVisible = false;
  let selectedJob = null;

  const dispatch = createEventDispatcher();

  onMount(async () => {
    await fetchData();
    tableVisible = true;
  });

  async function fetchData() {
    const response = await fetch("https://api.recruitly.io/api/job?apiKey=TEST64518616D4CF145D4E20BD47169EA7229BA3");
    const responseData = await response.json();
    jsonData = responseData.data;
  }

  function handleTitleClick(job) {
    selectedJob = job;
    dispatch("showPopup");
  }
</script>

<style>
  @import 'bootstrap/dist/css/bootstrap.min.css';

  .popup {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .popup-content {
    background-color: rgb(242, 243, 244);
    padding: 20px;
    border-radius: 5px;
  }
</style>

<main class="container mt-4">
  {#if tableVisible}
    <table class="table">
      <thead class="thead-light">
        <tr>
          <th>ID</th>
          <th>Title</th>
          <th>Reference</th>
          <th>Status</th>
          <th>Industry</th>
        </tr>
      </thead>
      <tbody>
        {#each jsonData as job}
          <tr>
            <td>{job.id}</td>
            <td>
              <a href="#" on:click|preventDefault={() => handleTitleClick(job)}>{job.title}</a>
            </td>
            <td>{job.reference}</td>
            <td>{job.status}</td>
            <td>{job.industry}</td>
          </tr>
        {/each}
      </tbody>
    </table>
  {/if}
</main>

{#if selectedJob}
<div class="popup">
  <div class="popup-content">
    <h2>{selectedJob.title}</h2>
    <p>ID: {selectedJob.id}</p>
    <p>Reference: {selectedJob.reference}</p>
    <p>Status: {selectedJob.status}</p>
    <p>Industry: {selectedJob.industry}</p>
    <button class="btn btn-primary" on:click={() => (selectedJob = null)}>Close</button>
  </div>
</div>
{/if}
=======
	import { onMount } from "svelte";
	import { createEventDispatcher } from "svelte";
  
	let jsonData = [];
	let tableVisible = false;
	let selectedJob = null;
  
	const dispatch = createEventDispatcher();
  
	onMount(async () => {
	  await fetchData();
	  tableVisible = true;
	});
  
	async function fetchData() {
	  const response = await fetch("https://api.recruitly.io/api/job?apiKey=TEST64518616D4CF145D4E20BD47169EA7229BA3");
	  const responseData = await response.json();
	  jsonData = responseData.data;
	}
  
	function handleTitleClick(job) {
	  selectedJob = job;
	  dispatch("showPopup");
	}
  </script>
  
  <style>
	@import 'bootstrap/dist/css/bootstrap.min.css';
  
	.popup {
	  position: fixed;
	  top: 0;
	  left: 0;
	  width: 100%;
	  height: 100%;
	  background-color: rgba(0, 0, 0, 0.5);
	  display: flex;
	  justify-content: center;
	  align-items: center;
	}
  
	.popup-content {
	  background-color: rgb(242, 243, 244);
	  padding: 20px;
	  border-radius: 5px;
	}
  </style>
  
  <main class="container mt-4">
	{#if tableVisible}
	  <table class="table">
		<thead class="thead-light">
		  <tr>
			<th>ID</th>
			<th>Title</th>
			<th>Reference</th>
			<th>Status</th>
			<th>Industry</th>
		  </tr>
		</thead>
		<tbody>
		  {#each jsonData as job}
			<tr>
			  <td>{job.id}</td>
			  <td>
				<a href="#" on:click|preventDefault={() => handleTitleClick(job)}>{job.title}</a>
			  </td>
			  <td>{job.reference}</td>
			  <td>{job.status}</td>
			  <td>{job.industry}</td>
			</tr>
		  {/each}
		</tbody>
	  </table>
	{/if}
  </main>
  
  {#if selectedJob}
	<div class="popup">
	  <div class="popup-content">
		<h2>{selectedJob.title}</h2>
		<p>ID: {selectedJob.id}</p>
		<p>Reference: {selectedJob.reference}</p>
		<p>Status: {selectedJob.status}</p>
		<p>Industry: {selectedJob.industry}</p>
		<button class="btn btn-primary" on:click={() => (selectedJob = null)}>Close</button>
	  </div>
	</div>
  {/if}
  
>>>>>>> 66e8217341fe5c8a8fda7f7b6176adf6dd31256f
