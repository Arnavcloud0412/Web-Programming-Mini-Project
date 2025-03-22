<script>
    import { onMount } from 'svelte';
    import NavPanel from './NavPanel.svelte';
    let activeTab = 'Team Info';
    import { student } from './authStore.js';

    const handleTabChange = (event) => {
        activeTab = event.detail;
    };
    
    let showIntro = true;

    onMount(() => {
        setTimeout(() => {
            showIntro = false;
        }, 5000); // Match animation duration (6 seconds)
    });
</script>

<svelte:head>
    <!-- Pico CSS -->
    <link
        rel="stylesheet"
        href="https://cdn.jsdelivr.net/npm/@picocss/pico@1/css/pico.min.css"
    >
</svelte:head>

<style>
    .intro-overlay {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: var(--bg-color);
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 1000;
        animation: introAnimation 6s ease-out forwards;
    }

    .intro-content {
        text-align: center;
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
        0% { opacity: 0; transform: translateY(20px); }
        20% { opacity: 1; transform: translateY(0); }
        80% { opacity: 1; transform: translateY(0); }
        100% { opacity: 0; transform: translateY(-20px); }
    }
    .layout {
        display: grid;
        grid-template-columns: 1fr 3fr;
        margin-left: 20px;
        height: 97vh;
    }

    .sidebar {
        text-align: center;
        border-right: 2px solid #ccc;
        padding: 1rem;
        padding-right: 2rem;
        padding-top: 2rem;
    }

    .sidebar h2 {
        margin-bottom: 3rem;
        border-bottom: 2px solid #ccc;
    }

    .main-content {
        padding: 2rem;
        display: flex;
        flex-wrap: wrap;
        gap: 1rem;
        justify-content: center;
        background-color: var(--pico-background-color);
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
    <div class="layout">
    <!-- Sidebar -->
    <aside class="sidebar">
        <h2>Project Dashboard</h2>  
        <!-- Navigation Menu -->
        <NavPanel on:tabChange={handleTabChange} />
    </aside>
    <div class="main-content">
        {#if !student.subject}
            <h2>No Active Teams</h2><br>
            <p>You are not part of any active teams.</p>
        {:else}
            <!-- Main Content -->
            {#if activeTab === 'Team Info'}
                <h2>Team Info</h2>
                <p>Team info goes here...</p>
            {:else if activeTab === 'Project Details'}
                <h2>Project Details</h2>
                <p>Project details go here...</p>
            {:else if activeTab === 'Upload'}
                <h2>Upload</h2>
                <p>Upload form goes here...</p>
            {:else if activeTab === 'Grades'}
                <h2>Grades</h2>
                <p>Grades go here...</p>
            {:else if activeTab === 'Announcements'}
                <h2>Announcements</h2>
                <p>Announcements go here...</p>
            {/if}
        {/if}
    </div>
</div>
{/if}

