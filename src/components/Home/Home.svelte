<script lang="ts">
    import axios from "axios";
    import Navbar from "./../Navbar/Navbar.svelte";
    import {memojiBASE, NAVBAR_DATA} from "../../static-data/site-data";
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
    <div class="home">
        <img class="home__image" src={memojiBASE} alt="">
        <p class="home__welcome">Hi! I'm glad to see you here</p>
        <p>Navigate to <a href="/about">about</a> to start using app</p>
        <p class="home__github">My GitHub account: <a href="/about">elayLo</a> <span> <br>star the repo with this project</span></p>
    </div>
</main>

<style>
    .home {
        position: absolute;
        left: 0;
        top: 80px;
        width: 100%;
        height: calc(100% - 80px);
        background: #333;
    }
    .home__image {
        width: 300px;
        height: 300px;
    }
    .home__welcome {
        color: white;
        font-size: 20px;
        font-weight: 500;
    }
    .home__github {
        color: white;
    }
    .home__github a {
        color: white;
    }
    .home__github span {
        font-style: italic;
        opacity: 0.5;
    }
</style>
