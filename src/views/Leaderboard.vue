<template>
    <div>
        <div class="item top" name="green">
            <div class="value">
                <div class="name">
                    Team Name
                </div>
                <div class="text">
                    100
                </div>
            </div>
        </div>
        <div class="item top" name="black">
            <div class="value">
                <div class="name">
                    Team Name
                </div>
                <div class="text">
                    100
                </div>
            </div>
        </div>
        <div class="item top" name="dark-grey">
            <div class="value">
                <div class="name">
                    Team Name
                </div>
                <div class="text">
                    100
                </div>
            </div>
        </div>
        <div class="item" name="purple">
            <div class="value">
                <div class="name">
                    Team Name
                </div>
                <div class="text">
                    100
                </div>
            </div>
        </div>
        <div class="item" name="red">
            <div class="value">
                <div class="name">
                    Team Name
                </div>
                <div class="text">
                    100
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .item {
        position: relative;
        width: 50vw;
        height: 40vh;
        display: inline-block;
        border: 0px solid white;
        transition: all 0.2s ease-in-out
    }

    .item.top {
        width: 33.33vw;
        height: 60vh;
    }

    .item[name="green"] {
        background: green;
    }

    .item[name="black"] {
        background: #212121;
    }
    .item[name="purple"] {
        background: purple;
    }
    .item[name="red"] {
        background: red;
    }

    .item[name="dark-grey"] {
        background: #555;
    }

    .item:hover {
        border: 5px solid white;
    }

    .value {
        position: absolute;
        top: 150px;
        left: 0;
        height: 100%;
        width: 100%;
    }

    .item.top .value {
        top: 200px;
    }

    .value {
        color: white;
        font-size: 100px;
        text-align: center;
        line-height: 100px;
    }

    /* .item.fixed > .value { */
        /* line-height: 40vh; */
    /* } */

    .name {
        font-size: 50px;
        line-height: 50px;
    }
</style>
