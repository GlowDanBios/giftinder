<template>
    <div class="base-preloader">
        <div class="base-preloader-spinner"></div>
    </div>
</template>


<style scoped>
    .base-preloader {
        display: flex;

        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;

        background-color: rgba(255, 255, 255, 0.4);

        justify-content: center;
        align-items: center;
    }

    .base-preloader-spinner {
        width: 30px;
        height: 30px;
        border-radius: 50%;
        border: 5px dashed #5a5f73;
        animation: rotate ease-out 3s infinite;
    }

    @keyframes rotate {
        from {
            transform: rotate(0deg);
        }

        to {
            transform: rotate(360deg);
        }
    }
</style>

