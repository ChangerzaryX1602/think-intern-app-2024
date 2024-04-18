<script>
  import axios from "axios";

  let identifier = "";
  let password = "";
  const login = async () => {
    await axios.post("http://localhost:5000/login", {
      identifier,
      password
    }).then((response) => {
      console.log(response);
      alert("Login successful!");
      window.location.href = "/cat";
    }).catch((error) => {
      console.error(error);
      alert("Login failed!");
    });
  };
</script>

<div
  style="display: flex; justify-content: center; align-items: center; height: 100vh;"
>
  <form style="display: flex; flex-direction: column; align-items: center; width: 400px; padding: 10px; border: 1px solid #ccc; border-radius: 8px;">
    <h1 style="font-size: 2em;">Login</h1>
    <input type="text" placeholder="Username or Email" style="width: 100%; padding: 10px; margin-bottom: 15px; font-size: 1.2em;" bind:value={identifier}/>
    <input type="password" placeholder="Password" style="width: 100%; padding: 10px; margin-bottom: 15px; font-size: 1.2em;" bind:value={password}/>
    <button class="login-button" style="width: 100%; padding: 10px; font-size: 1.2em;" on:click={login}>Login</button>
    <a href="/register" style="margin-top: 10px;">Don't have an account? Register here</a>
  </form>
</div>

<style>
  /* Styling for the button */
  .login-button {
    background-color: #4caf50; /* Green */
    border: none;
    color: white;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    font-size: 16px;
    margin: 4px 2px;
    cursor: pointer;
  }

</style>
