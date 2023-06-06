<script lang="ts">
    import axios from "axios";
    import {NAVBAR_DATA} from "./static-data/site-data";
    import {Router, Link, Route} from "svelte-routing";
    import Home from "./components/Home/Home.svelte";
    import About from "./components/About/About.svelte";
    import Publish from "./components/Publish/Publish.svelte";
    export let url = ""
    const data = NAVBAR_DATA
    let value: string = ""
    $: {
        console.log(value);
    }
    const botToken: string = "6268625700:AAFkoocMjTpeEBG8bc_m3G7CenKzjDpFFLs"

    async function addPost(text: string) {
        let url: string = `https://api.telegram.org/bot${botToken}/sendMessage`
        const payload = {
            chat_id: "@testredaktora",
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
    <Router url={url}>
        <Route path="/">
            <Home/>
        </Route>
        <Route path="/about">
            <About/>
        </Route>
        <Route path="/publish">
            <Publish/>
        </Route>
    </Router>


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
