<script>
    import { fly, scale } from 'svelte/transition';
    import { quintOut, quadOut } from 'svelte/easing';
    import { Hamburger } from 'svelte-hamburgers';
    import platina from '$lib/platina.ttf'
    
    let open;
</script>

<div class="menu_tb" style="background-color: {open ? 'grey' : 'transparent'};">
    <Hamburger
        bind:open
        --color={open ? 'white' : 'black'}
    />
    <h1 style="color: {open ? 'white': 'black'};">Arch</h1>
</div>

{#if open}
    <div class="menu_opt" transition:fly={{ duration: 300, y: -500, opacity: 0, easing: quintOut }}>
        {#each ['/ Beranda', '/work Proyek', '/about Tentang'] as link}
            <a href={link.split(" ")[0]}>{link.split(" ")[1]}</a>
        {/each}
    </div>
    <hr class="menu_line" transition:scale={{ duration: 450, easing: quadOut, opacity: 1 }} />
{/if}

<style>
    @font-face {
      font-family: platina;
      src: url(/fonts/platina.ttf);
    }
    
    :global(body) {
        margin: 0;padding: 0;
        font-family: platina;
    }
    
    .menu_opt {
        text-align: center;
        display: flex;
        flex-direction: column;
        gap: 3rem;
        font-size: 1.5em;
        letter-spacing: 0.15em;
        padding: 1em;
        padding-top: 1rem;
        background-color: grey;
    }
    
    .menu_opt a {
        display: inline-block;
        color: black;
        text-decoration: none;
        font-size: 31px;
        color: white;
    }
    
    .menu_opt a:hover {
        text-decoration: underline;
    }
    
    .menu_line {
        height: .1rem;
        background-color: grey;
    }
    
    .menu_tb {
        position: relative;
        margin-left: 0;margin-top: -.8rem;
        display: flex;
        justify-content: space-between;
    }
    
    .menu_tb h1 {
        margin-right: .8rem;
        display: block;
        font-size: 38px;
        letter-spacing: .3rem;
        transition: color .5s;
    }
    
</style>