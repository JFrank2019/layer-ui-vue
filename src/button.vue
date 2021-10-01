<template>
    <button class="ui-button" :class="{ [`icon-${iconPosition}`]: true }">
        <svg v-if="icon" class="icon">
            <use :xlink:href="`#i-${icon}`"></use>
        </svg>
        <div class="content">
            <slot />
        </div>
    </button>
</template>

<script>
export default {
    name: 'ui-button',
    props: ['icon', 'iconPosition'],
};
</script>

<style lang="scss">
.ui-button {
    font-size: var(--font-size);
    height: var(--button-height);
    padding: 0 1em;
    border-radius: var(--border-radius);
    border: 1px solid var(--border-color);
    background: var(--button-bg);
    display: inline-flex;
    justify-content: center;
    align-items: center;
    vertical-align: middle;
    > .icon {
        order: 1;
        margin-right: .3em;
        margin-left: 0;
    }
    > .content {
        order: 2;
    }
    &:hover {
        border-color: var(--border-color-hover);
    }
    &:active {
        border-color: var(--button-active-bg);
    }
    &:focus {
        outline: none;
    }
    &.icon-right {
        > .icon {
            order: 2;
            margin-left: .3em;
            margin-right: 0;
        }
        > .content {
            order: 1;
        }
    }
}
</style>
