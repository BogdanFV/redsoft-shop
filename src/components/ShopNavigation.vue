<template>
    <nav class="nav">
        <a href="#" class="nav-logo__link">
            <img v-if="isHeader" src="../assets/theFamousLogo.svg" alt="Логотип">
            <img v-else src="../assets/theFamousLogoDark.svg" alt="Логотип">
        </a>
        <ul class="nav-list" :class="{ 'active': isNavOpen }">
            <li class="nav-item">
                <a href="#" class="nav-item__link">
                    <h5>Каталог</h5>
                </a>
            </li>
            <li class="nav-item"><a href="#" class="nav-item__link">
                    <h5>Доставка</h5>
                </a></li>
            <li class="nav-item"><a href="#" class="nav-item__link">
                    <h5>Оплата</h5>
                </a></li>
            <li class="nav-item"><a href="#" class="nav-item__link">
                    <h5>Контакты</h5>
                </a></li>
            <li class="nav-item"><a href="#" class="nav-item__link">
                    <h5>О галерее</h5>
                </a></li>
        </ul>
        <div class="nav-toggle" @click="toggleNav">
            <img class="nav-toggle__img" v-if="isNavOpen" src="../assets/icons/close-icon.svg" alt="close">
            <img class="nav-toggle__img" v-else src="../assets/icons/menu-icon.svg" alt="open">
        </div>
    </nav>
</template>

<script>
export default {
    props: {
        isHeader: {
            type: Boolean,
            required: false,
        },
    },
    data() {
        return {
            isNavOpen: false,
        };
    },
    methods: {
        toggleNav() {
            this.isNavOpen = !this.isNavOpen;
        },
    },
};
</script>

<style lang="scss">
@import '../styles/colors';

.nav {
    display: flex;
    flex-direction: row;

    .nav-logo__link {
        display: flex;

    }

    .nav-list {
        display: flex;
        list-style: none;
        margin-left: 48px;
        
        &.active {
            position: absolute;
            left: 12px;
            top: 64px;
            width: 100px;

            align-items: center;
            justify-content: center;
            display: flex;
            flex-direction: column;
            background:  $primary-brown;

            .nav-item {
                margin: 12px 0;
                .nav-item__link {
                    color: white;
                }
            }
        }

        .nav-item {
            margin-right: 48px;
            display: flex;
            align-items: center;

            &:last-child {
                margin-right: 0;
            }

            .nav-item__link {
                text-decoration: none;
                color: $text-brown;
                display: flex;

                &:hover {
                    color: $secondary-brown;
                }
            }
        }

    }

    .nav-toggle {
        display: none;
        height: 34px;
        width: 34px;

        &:hover {
            cursor: pointer;
        }
    }

}

@media screen and (max-width: 1240px) {

    .nav {

        .nav-list {
            margin-left: 24px;

            .nav-item {
                margin-right: 24px;
                display: flex;
                align-items: center;
            }

        }

    }
}

@media screen and (max-width: 980px) {
    header {
        .nav {
            .nav-list {
                flex-wrap: wrap;
                justify-content: space-around;
                row-gap: 10px;
            }
        }
    }

    footer {
        .nav {
            .nav-logo__link {
                display: none;
            }
        }
    }

}

@media screen and (max-width: 540px) {
    header {
        .nav {
            .nav-list {
                display: none;
            }

            .nav-logo__link {
                display: none;
            }

            .nav-toggle {
                display: block;
                height: 34px;
                width: 34px;
                margin-right: 30px;
            }
        }
    }

    footer {
        .nav {
            .nav-logo__link {
                display: none;
            }

            .nav-list {
                flex-wrap: wrap;
                justify-content: space-around;
                row-gap: 10px;
                margin-left: 0;
            }
        }
    }

}
</style>
  