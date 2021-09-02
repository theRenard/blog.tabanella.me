<script lang="tsx">
import 'reflect-metadata';
import { Component, Vue } from "nuxt-property-decorator";
import { RButton } from '@therenard/renard-ui';
import PostList from "~/components/Posts/PostList.vue";

@Component({
  layout: 'admin',
})
export default class Index extends Vue {

  buttonHandler() {
    this.$router.push('admin/new-post')
  }

  render(): Vue.VNode {
    return (
        <div class="admin-page">
          <section class="new-post">
            <RButton vOn:click={this.buttonHandler}>
              Create Post
            </RButton>
          </section>
          <section class="existinig-posts">
            <h1>Existing Posts</h1>
            <PostList />
          </section>
        </div>
    );
  }
}
</script>