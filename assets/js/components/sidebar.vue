<style lang="scss" module>
    @import '~styles/components/light-component';

    .sidebar {
        @include light-component;

        ul {
            li a:hover {
                background: $blue-component-link-hover;
            }
        }
    }
</style>

<template>
    <div :class="[$style.sidebar, 'mb-5', 'p-3']"
        :style="{ width: collapsed ? '70px': 'auto'}"
    >
        <h5 class="text-center">
            Categories
        </h5>
        <ul class="nav flex-column mb4">
            <li class="nav-item">
                <a
                    class="nav-link"
                    href="/"
                >All Products</a>
            </li>
            <li
                v-for="(category, index) in categories"
                :key="index"
                class="nav-item"
            >
                <a
                    class="nav-link"
                    :href="category.link"
                >{{ category.name }}</a>
            </li>
        </ul>

        <hr>

        <div class="d-flex justify-content-end">
            <button
                class="btn btn-secondary btn-sm"
                @click="toggleCollapsed"
                v-text="collapsed ? '>>' : '<< Collapse'"
            >
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Sidebar',
    data() {
        return {
            collapsed: false,
            categories: [
                {
                    name: 'Dot Matrix Printers',
                    link: '#',
                },
                {
                    name: 'Iomega Zip Drives',
                    link: '#',
                },
            ],
        };
    },
    created() {
        console.log(this);
    },
    props: {
        testProp: {
            type: String,
            default: 'Hello',
        },
    },
    methods: {
        toggleCollapsed() {
            this.collapsed = !this.collapsed;
        },
    },
};
</script>
