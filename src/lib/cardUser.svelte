
<script>
    import Button from "./Button.svelte";

    export let photo
    export let name

    const texts = ['Daily', 'Weekly', 'Monthly']

</script>

<div class="user">
    <div class="user__top">
        <img class="user__icon" src={photo} alt='foto de avatar de {name}'>
        <div class="user__name">
            <span>Report for</span>
            <span>{name}</span>
        </div>
    </div>
    <div class="user__bottom">
        {#each texts as text}
            <Button {text} />
        {/each}
    </div>
</div>

<style lang="scss">

    .user{
        background-color: $neutral-Dark-blue;
        border-radius: $radius;
        font-weight: 300;

        @include desktop {
            width: 250px;
        }

        .user__top{
            background-color: $primary-Blue;
            display: flex;
            align-items: center;

            gap: 1rem;

            border-radius: $radius;
            padding: $padding;
            color: white;

            @include desktop{
                flex-direction: column;
                align-items:  start;

                gap: 1.4rem;
                height: 20rem;

            }

            .user__icon{
                border-radius: 50%;
                width: 70px;
                height: 70px;

                border: 3px solid white;
                object-fit: cover;
            }

            .user__name{
                display: flex;
                flex-direction: column;

                span:nth-child(1){
                    color: $neutral-Pale-blue;
                }

                span:nth-child(2){
                    font-size: 1.8rem;

                    @include desktop{
                        font-size: 2.7rem;
                    }
                }
            }
        }

        .user__bottom{
            display: flex;
            justify-content: space-between;
            align-items: center;

            padding: $padding;

            @include desktop{
                flex-direction: column;
                align-items: start;

                gap: 1.3rem;
            }
        }
    }
</style>