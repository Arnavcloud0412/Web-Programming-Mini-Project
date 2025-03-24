<script>
    import { onMount } from 'svelte';
    import { fade, scale } from 'svelte/transition';
    
    import NavPanel from './NavPanel.svelte';
    import { student } from './authStore.js';  // Adjust to your actual store/path

    let showIntro = true;
    let expandedSubject = null; // tracks which subject is expanded, if any


    // Hide intro overlay after 5 seconds
    onMount(() => {
        setTimeout(() => {
            showIntro = false;
        }, 5000);
    });

    // When a card is clicked, set the expanded subject
    function handleCardOpen(subjectName) {
        expandedSubject = subjectName;
    }

    // Close the expanded subject view
    function handleCardClose() {
        expandedSubject = null;
    }
</script>

<!-- Optional Pico CSS -->
<svelte:head>
    <link
        rel="stylesheet"
        href="https://cdn.jsdelivr.net/npm/@picocss/pico@1/css/pico.min.css"
    >
</svelte:head>

<style>
    /* INTRO OVERLAY ANIMATION */
    .intro-overlay {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: var(--bg-color, #222);
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 1000;
        animation: introAnimation 6s ease-out forwards;
    }
    .intro-content {
        text-align: center;
        color: #fff;
        opacity: 0;
        animation: contentFade 4s ease-in-out;
    }
    @keyframes introAnimation {
        0% {
            opacity: 1;
            transform: scale(1);
        }
        90% {
            opacity: 1;
            transform: scale(1);
        }
        100% {
            opacity: 0;
            transform: scale(1.5);
        }
    }
    @keyframes contentFade {
        0%   { opacity: 0;   transform: translateY(20px); }
        20%  { opacity: 1;   transform: translateY(0);     }
        80%  { opacity: 1;   transform: translateY(0);     }
        100% { opacity: 0;   transform: translateY(-20px); }
    }

    /* LAYOUT */
    .layout {
        display: grid;
        grid-template-columns: 400px 1fr; /* side nav width + main content */
        height: 100vh;
    }
    .sidebar {
        text-align: center;
        border-right: 2px solid #ccc;
        padding: 2rem;
        background-color: var(--pico-background-color);
        width: 100%;
    }
    .sidebar h2 {
        margin-bottom: 2rem;
        border-bottom: 2px solid #ccc;
    }

    /* MAIN CONTENT */
    .main-content {
        position: relative; /* for overlay positioning */
        padding: 2rem;
        display: flex;
        flex-direction: column;
        gap: 1rem;
        justify-content: center;
        background-color: var(--pico-background-color, #fff);
        overflow: hidden;
    }
    .subject-header {
        text-align: center;
        margin-bottom: 1rem;
    }
    .subject-cards {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .scroll-content {
        display: flex;
        flex-wrap: wrap;
        gap: 1rem;
        justify-content: center;
    }
    .card {
        width: 200px;
        height: 180px;
        border-radius: 20px;
        border: 2px solid #ffffff;
        background-color: #02216269;
        color: #fff;
        display: flex;
        justify-content: center;
        align-items: center;
        cursor: pointer;
        text-align: center;
    }

    /* OVERLAY + EXPANDED PANEL */
    .overlay {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.3);
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .expanded-panel {
        background-color: #fff;
        width: 80%;
        height: 80%;
        border-radius: 8px;
        padding: 2rem;
        box-shadow: 0 0 20px rgba(0,0,0,0.2);
        overflow: auto;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
    }
    .expanded-panel h2 {
        margin-top: 0;
    }
</style>

{#if showIntro}
    <div class="intro-overlay">
        <div class="intro-content">
            <h1>Welcome to Project Dashboard</h1>
            <p>Loading your team workspace...</p>
        </div>
    </div>
{:else}
    <!-- MAIN DASHBOARD LAYOUT -->
    <div class="layout">
        <!-- Sidebar -->
        <aside class="sidebar">
            <h2>Project Dashboard</h2>
            <NavPanel/>
        </aside>
        
        <!-- Main content area -->
        <div class="main-content">
            {#if !expandedSubject}
                {#if !student.subjects}
                    <h2>No Active Teams</h2>
                    <p>You are not part of any active teams.</p>
                {:else}
                    <div class="subject-header">
                        <h2>Your Subjects</h2>
                    </div>
                    <div class="subject-cards">
                        <div class="scroll-content">
                            {#each Object.entries(student.subjects) as [subjectName]}
                                <button
                                    class="card"
                                    on:click={() => handleCardOpen(subjectName)}
                                    transition:scale={{ duration: 200 }}
                                >
                                    <h3>{subjectName}</h3>
                                </button>
                            {/each}
                        </div>
                    </div>
                {/if}
            {:else}
                <!-- Overlay for expanded subject -->
                <div class="overlay" transition:fade={{ duration: 200 }}>
                    <div class="expanded-panel" transition:scale={{ duration: 200 }}>
                        <h2>{expandedSubject}</h2>
                        <p>Here’s some detailed content about {expandedSubject}...</p>
                        <button on:click={handleCardClose}>Close</button>
                    </div>
                </div>
            {/if}
        </div>
    </div>
{/if}
