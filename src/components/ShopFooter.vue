<template>
    <footer class="footer">
        <div class="footer-container container">
            <ShopNavigation />
            <div class="footer-contact">
                <div class="footer-contact__phone">
                    <img src="../assets/icons/phone-icon.svg" alt="phone" class="footer-contact__phone-icon" />
                    <h5 class="footer-contact__phone-number">+7 (495) 555-55-55</h5>
                </div>
                <div class="footer-contact__location">
                    <img src="../assets/icons/location-icon.svg" alt="location" class="footer-contact__location-icon" />
                    <h5 class="footer-contact__location-address">г. Москва, ул. Расплетина, 24</h5>
                </div>
            </div>
        </div>
    </footer>
</template>
  
<script>
import ShopNavigation from './ShopNavigation.vue';

export default {
    components: {
        ShopNavigation,
    },
};
</script>
  
<style lang="scss">
.footer {
    background: #ECEAEA;
    flex-shrink: 0;

    &-container {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;
        padding: 24px 0;

        .footer-contact {
            display: flex;
            flex-direction: row;
            align-items: center;


            &__phone {
                display: flex;
                align-items: center;

                &-icon {
                    padding-top: 2px;
                    margin-right: 9px;
                }

                &-number {
                    margin-right: 48px;
                }
            }

            &__location {
                display: flex;
                flex-direction: row;
                align-items: center;

                &-icon {
                    margin-right: 10px;
                }
            }
        }
    }
}


@media screen and (max-width: 1240px) {
    .footer-container {
        padding: 24px;

        .footer-contact {
            flex-direction: column;

            &__location {
                margin-top: 10px;
            }
        }
    }
}


@media screen and (max-width: 980px) {
    .footer-container {
        flex-direction: column;
        padding: 24px 0;

        .footer-contact {
            margin-top: 16px;
        }
    }

}

@media screen and (max-width: 866px) {
    .footer-container {
        flex-direction: column;

        .footer-contact {
            margin-top: 16px;


            &__phone {
                display: flex;
                align-items: center;

                &-icon {
                    padding-top: 2px;
                    margin-right: 9px;
                }

                &-number {
                    margin-right: 24px;
                }
            }

            &__location {

                &-icon {
                    margin-right: 10px;
                }
            }
        }
    }
}

@media screen and (max-width: 460px) {}
</style>
  