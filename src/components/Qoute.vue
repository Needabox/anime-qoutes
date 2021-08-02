<template>
    <section class="qoute">
        <div class="qoute-content">
            {{ qoute.content }}
        </div>
        <div class="qoute-info">
            <div class="qoute-anime">
                {{ qoute.anime }}
            </div>
            <div class="qoute-author">
                {{ qoute.character }}
            </div>
        </div>
    </section>
</template>

<script>
export default {
    props: ['qoute']
}
</script>

<style lang="scss" scoped>
    .qoute {
        position: relative;
        margin: 0 auto;
        padding: 32px;
        max-width: 720px;

        &-content {
            position: relative;
            font-size: 28px;
            font-weight: 600;
            background-color: var(--dark);
            color: var(--light);
            padding: 48px 32px;
            border-radius: 16px;

            &:before,&:after {
                content: " '' ";
                color: var(--grey);
                margin: 0px 2px;

            }
        }

        &-info {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            padding: 32px;

            .qoute-author, .qoute-anime {
                position: absolute;
                padding: 12px 16px;
                font-size: 24px;
                font-weight: 700;
                border-radius: 99px;
                color: var(--light);
                text-align: center;
            }

            .qoute-author {
                top: calc(100% - 32px);
                right: 0;
                transform: translateY(-50%);
                background-color: var(--secondary);
            }

            .qoute-anime {
                top: 0px;
                left: opx;
                background-color: var(--tertiary);
                color: var(--dark);
            }
        }
    }
</style>