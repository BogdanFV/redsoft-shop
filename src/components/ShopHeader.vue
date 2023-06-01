<template>
    <header class="header">
        <div class="container header-container">
            <ShopNavigation :isHeader="true" />
            <div class="header-search">
                <input class="header-search__input" type="text" placeholder="Поиск по названию картины" v-model="searchText"
                    @keyup.enter="handleSearch" />
                <button class="header-search__btn" @click="handleSearch">
                    <h4>Найти</h4>
                </button>
            </div>
        </div>
    </header>
</template>
  
<script>
import ShopNavigation from './ShopNavigation.vue';

export default {
    components: {
        ShopNavigation,
    },
    data() {
        return {
            searchText: '',
        };
    },
    methods: {
        handleSearch() {
            this.$emit('search', this.searchText);
        },
    },
};
</script>
  
<style lang="scss">
@import '../styles/button';

.header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-bottom: 1px solid #e1e1e1;

    &-container {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;
        padding: 24px 0;

        .header-search {
            display: flex;
            flex-direction: row;
            height: 48px;

            &__input {
                border: 1px solid #e1e1e1;
                height: 48px;
                padding-left: 16px;
                width: 294px;

                font-family: 'Merriweather';
                font-weight: 400;
                font-size: 14px;
                line-height: 150%;
                color: #343030;

                &::placeholder {
                    color: #9f9f9f;
                }

                &:focus {
                    outline: none;

                    &::placeholder {
                        color: #bfbfbf;
                    }
                }
            }
        }
    }
}

@media screen and (max-width: 1240px) {
    .header {

        &-container {
            display: flex;
            flex-direction: row;
            justify-content: space-between;
            align-items: center;
            padding: 24px 20px;

            .header-search {
                height: 48px;

                &__input {
                    height: 48px;
                    padding-left: 16px;
                    width: 294px;

                    font-family: 'Merriweather';
                    font-weight: 400;
                    font-size: 14px;
                    line-height: 150%;
                    color: #343030;

                    &::placeholder {
                        color: #9f9f9f;
                    }

                    &:focus {
                        outline: none;

                        &::placeholder {
                            color: #bfbfbf;
                        }
                    }
                }
            }
        }
    }
}


@media screen and (max-width: 980px) {
    .header {
        &-container {
            .header-search {
                &__input {
                    width: 200px;

                    &::placeholder {
                        font-size: 10px;
                    }
                }
            }
        }
    }
}

@media screen and (max-width: 866px) {
    .header-container {
        flex-direction: column;

        .header-search {
            margin-top: 16px;

            &__input {
                width: 370px;
            }
        }
    }
}

@media screen and (max-width: 540px) {

    .header-container {
        flex-direction: row;

        .header-search {
            margin-top: 0;
            height: 36px;

            &__input {
                width: 240px;
                height: 36px;
            }
        }
    }
}

@media screen and (max-width: 460px) {

    .header-container {

        .header-search {
            height: 36px;

            &__input {
                width: 180px;
                height: 36px;
            }
        }
    }
}
</style>
  