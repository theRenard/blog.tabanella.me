<script lang="tsx">
import 'reflect-metadata';
import { RButton, RInput } from '@therenard/renard-ui';
import { Component, Vue, Prop } from "nuxt-property-decorator";
import { Post } from '~/types/posts.d';

@Component
export default class Index extends Vue {

  @Prop({
    type: Object as Vue.PropType<Post>,
    required: false
  })
  post!: Post;

  editedPost: Post = this.post ? { ...this.post } : {
    id: 0,
    author: '',
    title: '',
    thumbnailLink: '',
    content: '',
  };


  onCancel() {
    this.$router.push('/admin');
  }

  onSave() {
    this.$emit('submit', this.editedPost);
  }

  render(): Vue.VNode {
    // console.log(test);
    return (
      <form vOn:submit_prevent={this.onSave}>
        <RInput vModel={this.editedPost.author}>Author Name</RInput>
        <RInput vModel={this.editedPost.title}>Title</RInput>
        <RInput vModel={this.editedPost.thumbnailLink}>Thumbnail Link</RInput>
        <RInput
          control-type="textarea"
          vModel={this.editedPost.content}>
          Content
        </RInput>
        <RButton type="submit">Save</RButton>
        <RButton
          type="button"
          style="margin-left: 10px"
          btn-style="cancel"
          vOn:click={this.onCancel}>
          Cancel
        </RButton>
      </form>
    );
  }

}
</script>