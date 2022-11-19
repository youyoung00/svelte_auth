<script>
    // import {onMount} from 'svelte';
    import {authenticated} from '../stores/auth';

    let message = ''

    // onMount(async () => {
    //     try {
    //         const response = await fetch('http://localhost:8000/api/user', {
    //             headers: {'Content-Type': 'application/json'},
    //             credentials: 'include',
    //         });

    //         const content = await response.json();

    //         message = `Hi ${content.name}`;
    //         // $authenticated.set(true);
	// 		$authenticated = true;
    //     } catch (e) {
			
    //         message = 'You are not logged in';
	// 		$authenticated = false;
    //         // $authenticated.set(false);
    //     }
    // });

	async function authChecker () {
		if ($authenticated) {
		const response = await fetch('http://localhost:8000/api/user', {
                headers: {'Content-Type': 'application/json'},
                credentials: 'include',
            });

            const content = await response.json();

            message = `Hi ${content.name}`;
            // $authenticated.set(true);
			// $authenticated = false;
		} else {
			message = 'You are not logged in';
			// $authenticated = true;
		}
	}

	authChecker();

</script>

{message}