<template>
    <div class="search" 
        :style= "[
          routeName === 'Transportation' ? styleA : styleB
      ]"
    >
        <div class="search__search">
            <div class="search__grid">
                <div class="search__address">
                    <input type="text" placeholder="location">
                </div>
                <div class="search__grid-middle">
                    <div class="search__date">
                        <!-- <vc-date-picker 
                            mode='range'
                            v-model='range'
                            :columns="$screens({ default: 1, lg: 2 })"
                            :input-props='{
                                style: "height: 46px; background-color: #EEEEEE; border-radius: 8px; border: none; font-size: 14px;",
                                placeholder: this.date,
                                readonly: true
                            }'
                        /> -->
                        <vc-date-picker v-model="date">
                            <template v-slot="{ inputValue, inputEvents }">
                                <input
                                class="search__calendar"
                                :value="inputValue"
                                v-on="inputEvents"
                                />
                            </template>
                        </vc-date-picker>
                    </div>
                    <div class="search__guests">
                        <input type="text" placeholder="2 guests">
                    </div>
                    <div class="search__time">
                        <input type="text" placeholder="7:00pm">
                    </div>
                </div>
                </div>
            <div class="search__search-button">
                <router-link to="/deep-search">
                    <button class="search__button">
                        <i class="fas fa-search"></i>
                    </button>
                </router-link>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Search",
    props: {
        routeName: String
    },
    data: function () {
        return {
            date: new Date(),
            range: {
                start: new Date(), // Jan 16th, 2018
                end: new Date()    // Jan 19th, 2018
            },
            styleA: {
                // backgroundColor: 'orange',
                // position: "-webkit-sticky",
                // position: "sticky",
                // top: "62px"
            },
            styleB: {
                // backgroundColor: 'red'
            }
        }
    },
    mounted() {
    },
    computed: {},
    methods: {}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.search {

    margin: auto;

    &__search {
        width: 95%;
        margin: auto;

        @media (min-width: 570px) {
           width: 100%;
           margin: 0;
        }

        @media (min-width: 1024px) {
            display: flex;
            align-items: baseline;
            justify-content: space-between;
            width: auto;
        }
    }

    &__grid {
        display: flex;
        flex-direction: column;

        @media (min-width: 1024px) {
           flex-direction: row;
            width: 100%;
        }
    }

    &__address {
        @media (min-width: 1024px) {
            width: 55%;
            margin-right: 5px;
        }
    }

    &__grid-middle {
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;

        @media (min-width: 570px) {
           flex-wrap: nowrap;
            align-items: baseline;
        }

        @media (min-width: 1024px) {
            margin-right: 5px;
        }
    }

    &__date {
        width: 100%;
        margin-top: 5px;

        @media (min-width: 570px) {
            margin: 0px 5px 0px 0px;
        }
    }

    &__guests {
        width: 100%;
        @media (min-width: 570px) {
            margin: 0px 5px 0px 0px;
        }
    }

    &__time {   
        width: 100%;
    }

    &__calendar {
        height: 46px; 
        background-color: #EEEEEE; 
        border-radius: 8px; 
        border: none; 
        font-size: 14px;
        padding: 12px 20px;
        width: 100%;
    }

    input[type=text] {
        width: 100%;
        padding: 12px 20px;
        margin-top: 5px;
        height: 46px;
        background-color: #EEEEEE;
        border: 0;
        border-radius: 8px;
    }

    input[type=date] {
        width: 100%;
        padding: 12px 20px;
        margin-top: 5px;
        height: 46px;
        background-color: #EEEEEE;
        border: 0;
        border-radius: 8px;
        color: #000;
    }

    ::placeholder {
        color: #212a30;
    }

    &__button {
        width: 100%;
        padding: 12px 20px;
        height: 46px;
        margin-top: 10px;
        background-color: #339DBE;
        border: 0;
        border-radius: 8px;
        color: #fff;
    }

}


</style>