<template>
    <div>
        <select @change="onChange($event)">
            <option value="">Please select one</option>
            <option value="junior">Junior</option>
            <option value="professional">Professional</option>
            <option value="senior">Senior</option>
            <option value="principal">Principal</option>
        </select>
    </div>
</template>

<script>
  export default {
    name: "LevelChooser",
    props: {
    },
    methods: {
        onChange(event) {
            this.$emit('role-change', event.target.value)
        }
    }
  };
</script>