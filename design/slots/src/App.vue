<template>
  <div>
      <ul>
            <item>
                아이템1
            </item>
            <item>
                아이템2
                <button>click me</button>
            </item>
            <item>
                <div>
                    아이템3
                </div>
                <img src="" alt="이미지" width="50px;" height="50px;">
            </item>
            <item>
                <div style="color: blue; font-size: 20px;">아이템4</div>
            </item>
      </ul>
  </div>
</template>

<script>
import Item from './components/Item.vue';

export default {
    components: {
        Item
    }
}
</script>