<script>
  import '../app.css';
  import * as config from "$lib/config.js";
  import 'iconify-icon'
  import { onMount } from 'svelte'
  import { themeChange } from 'theme-change'
  import { onNavigate } from "$app/navigation";

  onNavigate((navigation) => {
    if (!document.startViewTransition) return;

    return new Promise((resolve) => {
      document.startViewTransition(async () => {
        resolve();
        await navigation.complete;
      });
    });
  });

  onMount(() => {themeChange(false)})
</script>

<svelte:head>
        <title>{config.name} - Bio</title>
  <link rel="icon" href="{config.favicon}" />
</svelte:head>

<div class="navbar bg-base-200 drop-shadow-md sticky top-0 z-50">
  <div class="flex-1">
    <a href="/" class="btn btn-ghost text-xl">
    <div class="avatar mr-2">
        <div class="w-8 rounded-full">
          <img src="{config.profileLink}" alt="Profile"/>
        </div>
      </div>
      {config.name}</a>
  </div>
  <div class="flex-none">
    <ul class="menu menu-horizontal px-1">
      <li>
        <!--
          <label class="swap swap-rotate">
            <input data-toggle-theme="black,wireframe" data-act-class="ACTIVECLASS" type="checkbox" class="theme-controller"/>
            <iconify-icon class="swap-on fill-current" height="20px" icon="ic:baseline-light-mode"/>
            <iconify-icon class="swap-off fill-current" height="20px" icon="ic:baseline-dark-mode"/>
          </label>
        -->
      </li>

      <li style="view-transition-name: about;">
        <a href="/about" aria-label="about">
          <iconify-icon height="20px" icon="ic:baseline-help"/>
        </a>
      </li>
    </ul>
  </div>
</div>

<slot />

<div class="toast toast-end p-2 sm:p-5">
  <a target="_blank" href="{config.kofiLink}" class="flex alert alert-success">
    <span><b>Donate</b></span>
  </a>
</div>
