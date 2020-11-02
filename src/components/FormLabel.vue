<script>
const FormLabel = props => {
  return (
    <label
      for="price"
      class="block text-sm font-medium leading-5 text-gray-700 text-left"
    >
      {props.label}
    </label>
  );
};

FormLabel.props = {
  label: {
    type: String,
    required: true
  }
};

export default FormLabel;
</script>
