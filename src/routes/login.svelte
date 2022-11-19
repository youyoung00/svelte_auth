
<script>

    import { goto } from "@sapper/app.mjs"
    import {authenticated} from "../stores/auth";

    let email = '', password = ''

    const submit = async () => {
        let res = await fetch('http://localhost:8000/api/login', {
            method: 'POST',
            headers: {'Content-Type': 'application/json'},
            credentials: 'include',
            body: JSON.stringify({
                email,
                password
            })
        });
        $authenticated = true;
        console.log(res);
        console.log(res);
        console.log(res);
        await goto('/')
    }
</script>

<form on:submit|preventDefault={submit}>
    
    <h1 class="h3 mb-3 fw-normal">Please sign in</h1>

    
        <input bind:value={email} type="email" class="form-control" placeholder="Email">
    
    
        <input bind:value={password} type="password" class="form-control" placeholder="Password">
        

    <button class="w-100 btn btn-lg btn-primary" type="submit">Sign in</button>
</form>
  
  