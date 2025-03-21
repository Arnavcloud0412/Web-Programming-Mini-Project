<script>
    export let register; // Accept `register` as a prop

    let email = '';
    let password = '';

    function handleSubmit() {
        // Handle login logic here
        console.log('Username:', email);
        console.log('Password:', password);
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

    .login-container {
        max-width: 400px;
        margin: 0 auto;
        padding: 1rem;
        border-radius: 4px;
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
        padding: 0.5rem;
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
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 2rem;
    }

    .left-side{
        flex: 1;
        padding: 2rem;
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        text-align: center;
    }

    .right-side{
        flex: 1;
        padding: 2rem;
        border: 2px solid #ccc;
        margin-left: 5rem;
        border-radius: 40px;
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

<div class="login">
    <div class="left-side">
        <h1>Welcome to Project Submission Portal</h1>
    </div>
    <div class="right-side">
        <div class="login-container">
            <h2>Login</h2>
            <form>
                <div class="form-group">
                    <label for="username">Email</label>
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