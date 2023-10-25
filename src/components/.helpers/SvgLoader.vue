<template>
    <div v-if="svgContent" v-html="svgContent"></div>
</template>
  
<script>
export default {
    name: 'SvgLoader',
    props: {
        svgFileName: {
            type: String,
            required: true
        }
    },
    data() {
        return {
            directoryPath: 'src/assets/icons',
            svgContent: null
        };
    },
    mounted() {
        const svgPath = `${this.directoryPath}/${this.svgFileName}`;
        fetch(svgPath)
            .then(response => response.text())
            .then(svg => {
                this.svgContent = svg;
            });
    }
}
</script>