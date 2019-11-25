<template>
    <div id="post" v-if="visible">
        <nuxt-link :to="'posts/' + id">
            <span id="post-title"> {{ title }} </span>
        </nuxt-link>
        <span id="post-description"> {{ description }} </span>
        <div id="post-data">
            <span> {{ likes }} Likes</span>
            <button class="button" @click="addLike">Add like</button>
            <span> {{ comments }} Comments</span>
            <button class="button" @click="addComment">Add comment</button>
        </div>

            <div id="tags">
                <div id="tag" v-for="tag in tags" :key="tag.id"> {{ tag }} </div>
            </div>
            <div id="tags-input">           
                <input class="text-input" v-model="newTag" />
                <button class="button" @click="addTag">Add tag</button>
            </div>

    </div>
</template>

<script>
export default {
    name: 'post',
    props: ['id', 'title', 'description', 'likes', 'comments', 'tags', 'visible'],
    data() {
        return {
            newTag: '',
        }
    },
    methods: {
        addLike: function() {
            this.$emit('addLike', this.id)
        },
        addComment: function() {
            this.$emit('addComment', this.id)
        },
        addTag: function() {
            if (this.newTag !== '') {
                this.$emit('tag', {'id': this.id, 'newTag': this.newTag});
                this.newTag = ''
            }
        }
    }
}
</script>

<style lang="less" scoped>
#post {
    padding: 20px;
    display: flex;
    flex-direction: column;
}
#post-data {
    margin-top: 10px;
    display: flex;
    flex-direction: row;
    align-items: center;
    flex-wrap: wrap;

    > span {
        margin-right: 10px;
    }
}
#post-interact {
    margin: 10px 0;
    display: flex;
    flex-direction: row;
    align-items: center;
}

#post-title {
    font-size: 24px;
}
#post-description {
    font-size: 16px;
}
#tags {
    margin-top: 10px;
    display: flex;
    flex-direction: row;
    align-items: center;
    flex-wrap: wrap;
}
#tag {
    background-color: #c6e3ff;
    padding: 4px 10px;
    margin: 3px 5px 3px 0;
    border-radius: 5px;
    font-size: 16px;
}
#tags-input {
    margin-top: 10px;
}
</style>