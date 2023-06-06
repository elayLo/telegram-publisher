<script>
    import {Link} from "svelte-routing";
    export let data
    export let active
    console.log(data)
</script>
<main>
    <div class="navbar">
        {#each data as item}
            <div class="navbar__item">
                {#if item.name === active}
                    <a href={item.url} class="navbar__item_active">{item.name}</a>
                {/if}

                {#if item.name !== active}
                    <a href={item.url}>{item.name}</a>
                {/if}

            </div>

        {/each}
    </div>
</main>
<style>
    .navbar {
        display: flex;
        justify-content: center;
        position: absolute;
        left: 0;
        top: 0;
        width: 100%;
        align-items: center;
        height: 80px;
    }
    .navbar__item a {
        color: black;
        padding: 20px 20px;
        margin-top: 20px;
    }
    .navbar__item a:hover {
        opacity: 0.3;
        transition: 0.3s;
    }
    .navbar__item_active {
        text-decoration: underline;
    }
</style>