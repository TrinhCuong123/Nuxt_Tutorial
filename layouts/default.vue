<template>
    <div class="app-wrapper">
      <header class="app-header">
        <nav>
          <ul>
            <li><NuxtLink to="/">Home</NuxtLink></li>
          </ul>
        </nav>
      </header>
      <main class="app-content">
        <slot />
      </main>
  
     
      </div>
</template>

<style>
  .app-wrapper {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }
  
  .app-header {
    background-color: #007bff;
    color: #fff;
    padding: 1rem;
  }
  
  .app-header nav ul {
    display: flex;
    list-style: none;
    margin: 0;
    padding: 0;
  }
  
  .app-header nav li {
    margin-right: 1rem;
  }
  
  .app-header nav a {
    color: #fff;
    text-decoration: none;
  }
  
  .app-content {
    flex-grow: 1;
    padding: 2rem;
  }

  </style>