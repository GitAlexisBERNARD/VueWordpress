<script setup lang="ts">
import { RouterLink } from 'vue-router'
</script>
<template>
    <header id="header">
        <div>
            <div>
                <div>
                    <a>
                        <img src="#" alt="Logo">
                    </a>
                </div>
                <div>
                    <ul>
                        <li>
                            <RouterLink to="/">Home</RouterLink>
                        </li>
                        <li>
                            <RouterLink to="/web3">Article portfolio</RouterLink>
                        </li>
                        <li>
                            <RouterLink to="/form">Form</RouterLink>
                        </li>
                    </ul>
            </div>
        </div>
    </div>
</header>
</template>