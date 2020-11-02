<script>
const FormLabel = props => {
  return (
    <label
      for={props.name}
      class="block text-sm font-medium leading-5 text-gray-700 text-left"
    >
      {props.label}
    </label>
  );
};

FormLabel.props = {
  name: {
    type: String,
    required: true
  },
  label: {
    type: String,
    required: true
  }
};

export default FormLabel;
</script>
