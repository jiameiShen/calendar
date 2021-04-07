<script type="text/babel">
  export default {
    name: "Item",
    props: {
      source: Object
    },
    render(h) {

      var {renderContent, _renderProxy} = this.$parent;

      return renderContent.call(_renderProxy, h, this.source);

    }
  }
</script>

