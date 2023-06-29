<script>
  let committees = [
    { id: 1, name: "Committee 1", description: "This is committee 1.", members: 100, lastJoined: '8 days ago', discussions: 20, libraries: 5 },
    { id: 2, name: "Committee 2", description: "This is committee 2.", members: 200, lastJoined: '15 days ago', discussions: 12, libraries: 3 },
    { id: 3, name: "Committee 3", description: "This is committee 3.", members: 150, lastJoined: '16 days ago', discussions: 10, libraries: 4 },
    { id: 4, name: "Committee 4", description: "This is committee 4.", members: 50, lastJoined: '28 days ago', discussions: 30, libraries: 7 },
    { id: 5, name: "Committee 5", description: "This is committee 5.", members: 220, lastJoined: '4 months ago', discussions: 25, libraries: 6 },
    { id: 6, name: "Committee 6", description: "This is committee 6.", members: 300, lastJoined: '1 year ago', discussions: 35, libraries: 8 }
  ];

  let search = '';
</script>

<style>
  * {
    box-sizing: border-box;
  }

  body {
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif;
  }

  .bg-gray-900 {
    background-color: #1F2937;
  }

  .bg-gray-100 {
    background-color: #F3F4F6;
  }

  .text-white {
    color: #FFFFFF;
  }

  .text-gray-300 {
    color: #D1D5DB;
  }

  .text-gray-700 {
    color: #4B5563;
  }

  .w-full {
    width: 100%;
  }

  .p-2 {
    padding: 0.5rem;
  }

  .border {
    border: none;
  }

  .rounded-lg {
    border-radius: 0.5rem;
  }

  .shadow-none {
    box-shadow: none;
  }

  .flex {
    display: flex;
  }

  .justify-between {
    justify-content: space-between;
  }

  .items-center {
    align-items: center;
  }

  .space-x-2 > :not(template) ~ :not(template) {
    --space-x-reverse: 0;
    margin-right: calc(0.5rem * var(--space-x-reverse));
    margin-left: calc(0.5rem * calc(1 - var(--space-x-reverse)));
  }

  .hover\:underline:hover {
    text-decoration: underline;
  }

  .container {
    max-width: 80%;
    margin-right: auto;
    margin-left: auto;
  }

  .text-4xl {
    font-size: 2.5rem;
    line-height: 3rem;
  }

  .font-bold {
    font-weight: bold;
  }

  nav ul {
    display: flex;
    margin: 0;
    padding: 0;
    list-style: none;
  }

  nav ul li {
    margin-right: 1rem;
  }

  .bg-gray-200 {
    background-color: transparent;
    border-bottom: 1px solid #000;
  }

  .text-2xl {
    font-size: 1.5rem;
    line-height: 2rem;
  }

  .mb-2 {
    margin-bottom: 0.5rem;
  }

  .mb-4 {
    margin-bottom: 1rem;
  }

  .mt-4 {
    margin-top: 1rem;
  }

  .md\:flex-row {
    flex-direction: row;
  }

  .md\:mt-0 {
    margin-top: 0;
  }

  .md\:ml-auto {
    margin-left: auto;
  }

  .gap-4 > :not(template) ~ :not(template) {
    --gap-reverse: 0;
    margin-inline-start: calc(1rem * calc(1 - var(--gap-reverse)));
    margin-inline-end: calc(1rem * var(--gap-reverse));
  }

  .text-3xl {
    font-size: 1.875rem;
    line-height: 2.25rem;
  }

  .h-screen {
    height: 100vh;
  }

  .grid {
    display: grid;
  }

  .grid-cols-1 {
    grid-template-columns: repeat(1, minmax(0, 1fr));
  }

  .md\:grid-cols-1 {
    grid-template-columns: repeat(1, minmax(0, 1fr));
  }

  .lg\:grid-cols-1 {
    grid-template-columns: repeat(1, minmax(0, 1fr));
  }

  .sticky {
    position: sticky;
    top: 0;
    z-index: 100;
  }
</style>

<header class="bg-gray-900 text-white sticky top-0 z-10" style="height: 25vh;">
  <div class="container mx-auto p-4 flex justify-between items-center">
    <div class="text-4xl font-bold">CUTA</div>
    <nav>
      <ul class="flex space-x-2">
        <li><a href="#" class="hover:underline text-gray-300">All Communities</a></li>
        <li><a href="#" class="hover:underline text-gray-300">Topic Communities</a></li>
        <li><a href="#" class="hover:underline text-gray-300">My Communities</a></li>
        <li><a href="#" class="hover:underline text-gray-300">Member Directory</a></li>
        <li><a href="#" class="hover:underline text-gray-300">APTA.com</a></li>
        <li><a href="#" class="hover:underline text-gray-300">Support</a></li>
        <li><a href="#" class="hover:underline text-gray-300">Join a Committee</a></li>
      </ul>
    </nav>
  </div>
</header>

<main class="flex flex-wrap h-screen bg-gray-100 justify-center">
  <div class="container p-8">
    <h2 class="text-3xl font-bold mb-8">All Communities</h2>
    <div class="grid grid-cols-1 md:grid-cols-1 lg:grid-cols-1 gap-4">
      {#each committees as committee (committee.id)}
        {#if committee.name.toLowerCase().includes(search.toLowerCase())}
          <div class="bg-gray-100 border-b-2 border-gray-300 p-6 flex flex-col md:flex-row">
            <div>
              <h3 class="text-2xl font-bold mb-2">{committee.name}</h3>
              <p class="text-gray-700 mb-4">{committee.description}</p>
              <p class="text-gray-700 mb-4">Last person joined {committee.lastJoined}</p>
            </div>
            <div class="flex items-center space-x-1 mt-4 md:mt-0 md:ml-auto">
              <button class="bg-gray-300 text-gray-700 py-1 px-2 text-sm rounded-sm">Discussions: <span class="text-gray-600">{committee.discussions}</span></button>
              <button class="bg-gray-300 text-gray-700 py-1 px-2 text-sm rounded-sm">Libraries: <span class="text-gray-600">{committee.libraries}</span></button>
              <button class="bg-gray-300 text-gray-700 py-1 px-2 text-sm rounded-sm">Members: <span class="text-gray-600">{committee.members}</span></button>
            </div>
          </div>
        {/if}
      {/each}
    </div>
  </div>
</main>
