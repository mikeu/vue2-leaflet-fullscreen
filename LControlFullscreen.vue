<script>
import { OptionsMixin, ControlMixin, propsBinder, optionsMerger } from 'vue2-leaflet';
import LeafletFullscreen from 'leaflet-fullscreen';
import 'leaflet-fullscreen/dist/leaflet.fullscreen.css';
export default {
  name: 'LControlFullscreen',
  mixins: [
    ControlMixin,
    OptionsMixin,
  ],
  mounted () {
    const options = optionsMerger({
      ...this.controlOptions,
      options: this.options,
    }, this);
    this.mapObject = new L.Control.Fullscreen(options);
    propsBinder(this, this.mapObject, this.$options.props);
    this.mapObject.addTo(this.$parent.mapObject);
  },
  render () {
    return null;
  },
};
</script>