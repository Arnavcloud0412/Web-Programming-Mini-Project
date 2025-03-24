<nav class="nav-menu">
    <h3 class="nav-item">Student Info</h3>
    <p>Name</p>
</nav>

<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/@picocss/pico@2/css/pico.min.css"
/>

<style>
    :root[data-theme='light'] {
        --bg-color: #ffffff;
        --text-color: #212529;
        --border-color: #ced4da;
        --highlight-color: #0d6efd; /* Or your preferred highlight color */
    }

    :root[data-theme='dark'] {
        --bg-color: #212529;
        --text-color: #f8f9fa;
        --border-color: #495057;
        --highlight-color: #0d6efd; /* Or your preferred highlight color */
    }

    /* 5) Navigation menu inside sidebar */
    nav.nav-menu {
        display: flex;
        flex-direction: column;
        gap: 2rem;
        flex-grow: 1;
    }

    /* 6) Each nav item */
    .nav-item {
        display: block;
        padding: 0.5rem 1rem;
        margin: 0.25rem 0;
        border-radius: 0.25rem;
        text-decoration: none;
        color: var(--text-color);
        transition: background-color 0.2s;
        background-color: var(--bg-color);
        border: none;
    }
</style>