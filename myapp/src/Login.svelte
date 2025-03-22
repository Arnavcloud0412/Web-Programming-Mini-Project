<script>
    export let register; // Accept `register` as a prop
    import StudentDashboard from './StudentDashboard.svelte';

    let email = '';
    let password = '';
    let showDashboard = false;

    function handleSubmit(event) {
        event.preventDefault(); // Prevent form submission reload

        if (email === "a@d" && password === "123") {
            console.log("Login successful!");
            showDashboard = true; // Show StudentDashboard
        } else {
            console.log("Invalid Credentials");
            alert("Invalid Credentials");
        }
    }
</script>

<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/@picocss/pico@2/css/pico.min.css"
/>

<style>

    :root {
        background-color: var(--pico-background-color);
    }

    .form-group {
        margin-bottom: 1rem;
    }

    label {
        display: block;
        margin-bottom: 0.5rem;
    }

    input {
        width: 100%;
        border: 1px solid #ccc;
        border-radius: 4px;
    }

    button {
        width: 100%;
        padding: 0.5rem;
        background-color: #007bff;
        color: white;
        border: none;
        border-radius: 4px;
        cursor: pointer;
    }

    button:hover {
        background-color: #0056b3;
    }

    .login{
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-top: 6rem;
        margin-left: 2rem;
        margin-right: 6rem;
    }

    .left-side{
        flex: 1;
        padding: 2rem;
        width: auto;
        display: flex;
        align-items: center;
        justify-content: center;
        text-align: center;
    }

    .right-side{
        border: 2px solid #ccc;
        border-radius: 40px;
        width: auto;
        padding: 2rem;
    }

    .register-btn{
        color: #007bff;
        background-color: transparent;
    }

    .register-btn:hover{
        color: #007bff;
        background-color: transparent;
    }
</style>

{#if showDashboard}
    <StudentDashboard />

{:else}
    <div class="login">
        <div class="left-side">
            <h1>Welcome to Project Submission Portal</h1>
        </div>
        <div class="right-side">
            <div class="login-container">
                <h2>Login</h2>
                <form>
                    <div class="form-group">
                        <label for="email">Email</label>
                        <input type="text" id="email" bind:value={email} required />
                    </div>
                    <div class="form-group">
                        <label for="password">Password</label>
                        <input type="password" id="password" bind:value={password} required />
                    </div>
                    <button type="submit" onclick={handleSubmit}>Login</button>
                    <div class="register">
                        <p>Don't have an account? <button type="button" onclick={register} class="register-btn">Register</button></p>
                    </div>
                </form>
            </div>
        </div>
    </div>
{/if}