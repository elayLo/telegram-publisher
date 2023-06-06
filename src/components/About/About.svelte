<script lang="ts">
    import axios from "axios";
    import Navbar from "../Navbar/Navbar.svelte";
    import {NAVBAR_DATA} from "../../static-data/site-data";
    const data = NAVBAR_DATA
    let value: string = ""
    $: {
        console.log(value);
    }

</script>

<main>
    <Navbar data={NAVBAR_DATA} active="About"/>
    About
    <div>
        <input type="text" placeholder="Type text " bind:value={value}>
        <button on:click={() => addPost(value)}>Press</button>
    </div>
    <h1>Vite + Svelte</h1>
</main>

<style>
    .logo {
        height: 6em;
        padding: 1.5em;
        will-change: filter;
        transition: filter 300ms;
    }

    .logo:hover {
        filter: drop-shadow(0 0 2em #646cffaa);
    }

    .logo.svelte:hover {
        filter: drop-shadow(0 0 2em #ff3e00aa);
    }

    .read-the-docs {
        color: #888;
    }
</style>
