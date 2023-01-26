<template>
   <header>
        <div class="logo">
            <router-link to="/"><img src="@/assets/images/logo.svg" alt="logo">Stable Diffusion</router-link>
        </div>
        <input type="checkbox" class="toggle" id="nav-toggle">
        <label for="nav-toggle" id="nav-toggle-label">
            <div class="bar"></div>
            <div class="bar"></div>
            <div class="bar"></div>
        </label>
        <nav>
            <ul>
                <li>
                    <router-link to="/">home</router-link>
                </li>
                <li>
                    <router-link to="/about">about</router-link>
                </li>
                <li>
                    <router-link to="/">gallery</router-link>
                </li>
                <li>
                    <router-link to="/">contacts</router-link>
                </li>
            </ul>
        </nav>
    </header>
</template>

<style scoped>

header {
    --header-bg: rgb(34,193,195);
    --header-bg-gradient: linear-gradient(0deg, rgba(34,193,195,1) 0%, rgba(253,187,45,1) 100%);
    
    position: fixed;
    top: 0;
    right: 0;
    left: 0;
    height: var(--nav-height);
    font-size: 1.5rem;
    display: grid;
    grid-auto-flow: column;
    grid-auto-columns: max-content;
    justify-content: space-between;
    align-content: center;
    color: var(--main-color);
    background: var(--header-bg);
    background: var(--header-bg-gradient);
    padding: 0 10%;
}

header ul {
    display: grid;
    grid-auto-flow: column;
    grid-auto-columns: max-content;
    grid-template-rows: 1fr;
    gap: .5rem;
    list-style: none;
    padding: 0 .5rem;
}

header a {
    display: flex;
    align-items: center;

    padding: 0 .5rem;
    border-radius: .25rem;
    text-decoration: none;
    color: var(--bg-color);
    color: #fdbb2d;
    background-color: var(--nav-btn-bg);
    text-transform: capitalize;
    transition: all var(--transition);
}

header a:hover {
    color: transparent;
    -webkit-text-stroke: 1px var(--main-color);
}

.logo {
    display: grid;
    place-content: center;
}

.logo a {
    background-color: inherit;
    color: var(--main-color);
    color: #F0A024;
    /* text-transform: uppercase; */
}

.logo a:hover {
    /* background-color: inherit; */
    color: #F0A024;
    -webkit-text-stroke: 0;
}

.logo a img  {
    margin-right: .5rem;
    width: 28px;
    height: auto;
}

#nav-toggle {
    display: none;
}

#nav-toggle-label {
    display: none;
    cursor: pointer;
}

@media screen and (max-width: 768px) {
    header {
        justify-content: space-between;
        align-items: center;
    }

    header nav {
        position: fixed;
        top: 0;
        bottom: 0;
        right: 0;
        width: 24rem;
        padding-top: var(--nav-height);
        background: var(--grey);
        border-radius: 1rem;

        clip-path: circle(calc(var(--nav-height) / 3) at calc(100% - var(--nav-height) / 2) calc(0% + var(--nav-height) / 2));
        transition: clip-path var(--transition-long);
    }

    header ul {
        grid-auto-flow: row;
        grid-template-columns: 1fr;
        grid-template-rows: none;
        gap: .5rem;
        padding: 0;
    }

    header a {
        padding: .5rem 1.5rem;
    }

    header a:hover {
        background-color: var(--bg-color);
    }

    #nav-toggle-label {
        --size: calc(var(--nav-height) / 3);
        --bar-height: 2px;

        display: flex;
        flex-direction: column;
        justify-content: space-between;
        flex-basis: auto;

        width: var(--size);
        height: var(--size);
        margin-right: var(--size);

        z-index: 1;
    }

    #nav-toggle-label .bar {
        display: inline-block;

        height: var(--bar-height);
        width: 100%;

        background-color: var(--bg-color);

        transition: transform var(--transition);
    }

    #nav-toggle:checked + #nav-toggle-label > .bar:nth-child(1) {
        transform: 
        translate(0, calc(var(--size) / 2 - var(--bar-height) / 2))
        rotate(225deg);
    }

    #nav-toggle:checked + #nav-toggle-label > .bar:nth-child(2) {
        transform: scaleX(0);
    }

    #nav-toggle:checked + #nav-toggle-label > .bar:nth-child(3) {
        transform: 
        translate(0, calc(-1 * var(--size) / 2 + var(--bar-height) / 2))
        rotate(135deg);
    }

    #nav-toggle:checked + * + nav {
        clip-path: circle(125vmax at 100% 0%);
    }

}

</style>