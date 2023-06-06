<script lang="ts">
    import axios from "axios";
    import Navbar from "./../Navbar/Navbar.svelte";
    import {NAVBAR_DATA} from "../../static-data/site-data";
    const data = NAVBAR_DATA
    let text: string = ""
    let key: string = ""
    let channel: string = ""

    async function addPost(text: string) {
        let url: string = `https://api.telegram.org/bot${key}/sendMessage`
        const payload = {
            chat_id: `@${channel}`,
            text: text,
            parse_mode: "MarkdownV2"
        }
        try {
            const response = await axios.post(url, payload);
            return response.data;
        } catch (error) {
            console.error(error);
        }
    }
</script>

<main>
    <Navbar data={NAVBAR_DATA} active="Home"/>
    <div>
        <p class="home__welcome">Hi! I'm glad to see you here</p>
        <p>Navigate to <a href="/about">about</a> to start using app</p>
        <p class="home__github">My GitHub account: <a href="/about">elayLo</a> <span> <br>star the repo with this project</span></p>
        <input type="text" placeholder="Type bot key here" bind:value={key}>
        <input type="text" placeholder="Type channel name here" bind:value={channel}>
        <input type="text" placeholder="Type post text here" bind:value={text}>
        <button on:click={() => addPost(text)}>Press</button>
    </div>
    <h1>Vite + Svelte</h1>
</main>

<style>
    .home__welcome {
        font-size: 20px;
        font-weight: 500;
    }
    .home__github {
        color: black;
    }
    .home__github a {
        color: black;
    }
    .home__github span {
        font-style: italic;
        opacity: 0.5;
    }
</style>
