<template>
    <div>
        <table class="table">
            <thead>
                <tr>
                <th>Definition</th>
                <th>Formula</th>
                <th>Answer</th>
                </tr>
            </thead>
             <tbody>
                <tr>
                <td>{{definition}}</td>
                <td>{{formula}}</td>
                <td>{{answer}}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    name:'Mytable',
    props: {
    definition: {
      type: String,
      default: '',
      required: false
    },
    formula: {
      type: String,
      default: '',
      required: false
    },
    answer: {
      type: Number,
      default: '',
      required: false
    }
    }
}
</script>