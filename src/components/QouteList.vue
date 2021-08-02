<template>
    <section class="qoute-list">
        <div class="qoute" v-for="(qoute,i) in qoutes.slice().reverse()" :key="i">
            <div class="qoute-content">
                {{ qoute.content }}
            </div>
        </div>
    </section>
</template>

<script>
export default {
    props: ['qoutes']
}
</script>

<style lang="scss" scoped>
    .qoute-list {
        padding: 32px;
        max-width: 720px;
        margin: 0 auto;

        .qoute {
            background-color: var(--light);
            padding: 16px;
            border-radius: 16px;
            margin-bottom: 16px;

            &-content {
                overflow: hidden;
                text-overflow: ellipsis;
                white-space: nowrap;
                line-height: 18px;
                max-height: 18px;
            }

            &:hover {
                .qoute-content {
                    white-space: unset;
                    max-height: unset;
                }
            }
        }
    }
</style>