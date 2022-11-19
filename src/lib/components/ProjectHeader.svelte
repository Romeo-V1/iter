<script lang='ts'>
    import Icon from "$lib/display/Icon.svelte";
    import { each } from "svelte/internal";
    import HammerScrewdriver from "svelte-material-icons/HammerScrewdriver.svelte";
    import ArrowExpand from "svelte-material-icons/ArrowExpand.svelte";
    import Settings from "svelte-material-icons/Settings.svelte";
    let tabs = [
        {
            name: "Project", 
            icon: HammerScrewdriver,
            selected: true,
        },
        {
            name: "Deployments",
            icon: ArrowExpand,
            selected: false,
        },
        {
            name: "Settings",
            icon: Settings,
            selected: false,
        },
    ]

    function switch_select (name: String) {
        tabs.forEach((tab) => {
            if (tab.name == name) {
                tab.selected = true;
            } else {
                tab.selected = false;
            }
        })
    }
</script>

<div class='header-wrapper'>
    {#each tabs as tab}
        <div on:click={() => switch_select(tab.name)} class={tab.selected === true ? "tab" : "tab selected"}>
            <Icon icon={tab.icon}/>
            <div class="text">
                {tab.name}
            </div>
        </div>
    {/each}
</div>


<style lang='stylus'>
@import "variables"
    
.header-wrapper
    display flex
    padding 0px 10px

.tab 
    display flex
    align-items center
    padding 8px
    cursor pointer
    &:hover
        background-color green
</style>