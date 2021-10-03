<template>
    <button class="ui-button" :class="{ [`icon-${iconPosition}`]: true }" @click="$emit('click')">
        <template v-if="icon && !loading">
            <ui-icon class="icon" :name="icon" />
        </template>
        <template v-if="loading">
            <ui-icon class="loading icon" name="loading" />
        </template>
        <span class="content">
            <slot />
        </span>
    </button>
</template>

<script>
import Icon from './icon';
export default {
    name: 'ui-button',
    components: {
        'ui-icon': Icon
    },
    props: {
        icon: {},
        loading: {
            type: Boolean,
            default: false,
        },
        iconPosition: {
            type: String,
            default: 'left',
            validator: (value) => !(value !== 'left' && value !== 'right'),
        },
    },
};
</script>

<style lang="scss">
@keyframes spin {
    0% {
        transform: rotate(0deg);
    }
    100% {
        transform: rotate(360deg);
    }
}
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
    .loading {
        animation: spin 1.5s linear infinite;
    }
}
</style>
