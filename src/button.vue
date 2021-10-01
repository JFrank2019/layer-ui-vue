<template>
    <button class="ui-button" :class="{ [`icon-${iconPosition}`]: true }">
        <template v-if="icon">
            <ui-icon :name="icon" />
        </template>
        <span class="content">
            <slot />
        </span>
    </button>
</template>

<script>
export default {
    name: 'ui-button',
    props: {
        icon: {},
        iconPosition: {
            type: String,
            default: 'left',
            validator: (value) => !(value !== 'left' && value !== 'right'),
        },
    },
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
        margin-right: 0.3em;
        margin-left: 0;
    }
    > .content {
        order: 2;
        display: block;
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
            margin-left: 0.3em;
            margin-right: 0;
        }
        > .content {
            order: 1;
        }
    }
}
</style>
