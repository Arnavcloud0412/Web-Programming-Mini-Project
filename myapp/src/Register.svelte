<script>
export let login

    let username = '';
    let password = '';
    let name = '';
    let email = '';
    let branch = '';
    let year = 0;
    let roll = 0;

    function handleSubmit() {
        // Handle login logic here
        console.log('Username:', username);
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

    .register{
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-top: 3rem;
        margin-left: 2rem;
        margin-right: 6rem;
        margin-bottom: 3rem;
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
        height: 125vh
    }

    .login-btn{
        color: #007bff;
        background-color: transparent;
    }

    .login-btn:hover{
        color: #007bff;
        background-color: transparent;
    }
</style>

<div class="register">
    <div class="left-side">
        <h1>Welcome to Project Submission Portal</h1>
    </div>
    <div class="right-side">
        <div class="register-container">
            <h2>Register</h2>
            <form>
                <div class="form-group">
                    <label for="name">Name</label>
                    <input type="text" id="name" bind:value={name} required />
                </div>
                <div class="form-group">
                    <label for="email">Email</label>
                    <input type="text" id="email" bind:value={email} required />
                </div>
                <div class="form-group">
                    <label for="password">Password</label>
                    <input type="password" id="password" bind:value={password} required />
                </div>
                <div class="form-group">
                    <label for="branch">Branch</label>
                    <input type="text" id="branch" bind:value={branch} required />
                </div>
                <div class="form-group">
                    <label for="year">Year</label>
                    <input type="number" id="year" bind:value={year} required />
                </div>
                <div class="form-group">
                    <label for="rollno">Roll No</label>
                    <input type="number" id="rollno" bind:value={roll} required />
                </div>
                <button type="submit" onclick={handleSubmit}>Register</button>
                <div class="login">
                    <p>Don't have an account? <button type="button" onclick={login} class="login-btn">Login</button></p>
                </div>
            </form>
        </div>
    </div>
</div>