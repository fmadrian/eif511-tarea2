<template>
    <span></span>
</template>
<script setup>

useServerHead({
    script: [
        {
            src: 'https://utteranc.es/client.js',
            repo: "fmadrian/eif511-tarea3",
            'issue-term': "pathname",
            label: "comments",
            theme: "github-light",
            crossorigin: "anonymous",
            body: true,
            async: true
        }
    ]
});
</script>