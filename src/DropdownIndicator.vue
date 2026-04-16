<template>
    <span class="icon dropdown-indicator"
        :class="indicatorClass"
        :aria-hidden="false">
        <fa :icon="faChevronRight"/>
    </span>
</template>

<script>
import { FontAwesomeIcon as Fa } from '@fortawesome/vue-fontawesome';
import { faChevronRight } from '@fortawesome/free-solid-svg-icons';

export default {
    name: 'DropdownIndicator',

    components: { Fa },

    data: () => ({
        faChevronRight,
    }),

    props: {
        open: {
            type: Boolean,
            default: false,
        },
        opensUp: {
            type: Boolean,
            default: false,
        },
    },

    computed: {
        indicatorClass() {
            return {
                'is-collapsed': !this.open,
                'is-open-up': this.open && this.opensUp,
                'is-open-down': this.open && !this.opensUp,
            };
        },
    },
};
</script>

<style lang="scss">
    .icon.dropdown-indicator {
        width: 0.5rem;
        height: 0.5rem;
        font-size: 0.8rem;
        line-height: 1;
        transition: transform .300s ease;
        transform: rotate(0deg);

        &.is-compact {
            width: 0.4rem;
            height: 0.4rem;
            font-size: 0.65rem;
        }

        &.is-collapsed {
            transform: rotate(0deg);
        }

        &.is-open-down {
            transform: rotate(90deg);
        }

        &.is-open-up {
            transform: rotate(-90deg);
        }
    }
</style>
