
<template>
    <header class="header">
        <div class="header__inner-wrapper">
            <div>
                <n-link to="/" no-prefetch>/
                </n-link>
            </div>
            <div>
                <n-link to="/schedule" no-prefetch>Schedule
                </n-link>
            </div>
            <div>
                <n-link to="/transport" no-prefetch>Transport</n-link>
            </div>
            <div>
                <n-link to="/special-requests" no-prefetch>Requests</n-link>
            </div>
        </div>
    </header>
</template>

<style lang="scss" scoped>
@import "~assets/styles/_variables.scss";
.header {
    width: 100%;
    height: auto;
    .header__inner-wrapper {
        display: flex;
        width: 50%;
        margin-left: auto;
        flex-wrap: wrap;
        font-family: $main-body-font;
        >div {
            flex: 1;
            justify-content: center;
            text-align: right;
            padding: $main-padding;
            a {
                color: $secondary-text-color;
            }
            a:hover {
                color: $main-accent-color;
                transition: color 0.5s ease;
            }
        }
    }
}
</style>