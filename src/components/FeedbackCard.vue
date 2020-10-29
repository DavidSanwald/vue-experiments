<script>
const FeedbackCard = props => {
  return (
    <div class="bg-white overflow-hidden shadow rounded-lg">
      <div class="px-4 py-5 sm:p-6">
        <dl>
          <dt class="text-sm leading-5 font-medium text-gray-500 truncate">
            {props.label}
          </dt>
          <dd class="mt-1 text-3xl leading-9 font-semibold text-gray-900">
            {props.value}
          </dd>
        </dl>
      </div>
    </div>
  );
};

FeedbackCard.props = ["value", "label"];

export default FeedbackCard;
</script>
