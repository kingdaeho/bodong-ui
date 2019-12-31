<template>
    <div id="app">
        <bodong-header></bodong-header>
        <bodong-input></bodong-input>
        <bodong-list></bodong-list>
        <BodongFooter></BodongFooter>
    </div>
</template>

<script>
    import BodongHeader from './components/BodongHeader'
    import BodongInput from './components/BodongInput'
    import BodongList from './components/BodongList'
    import BodongFooter from './components/BodongFooter'

    export default {
        components: {
            'BodongHeader': BodongHeader,
            'BodongInput': BodongInput,
            'BodongList': BodongList,
            'BodongFooter': BodongFooter
        }
    }
</script>

<style>
    body {
        text-align: center;
        background-color: #F6F6F8;
    }

    input {
        border-style: groove;
        width: 200px;
    }

    button {
        border-style: groove;
    }

    .shadow {
        box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03)
    }
</style>
