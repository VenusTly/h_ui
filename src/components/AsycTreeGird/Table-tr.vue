<template>
    <tr :class="rowClasses(row._index)"><slot></slot></tr>
</template>
<script>
  export default {
    props: {
      row: Object,
      prefixCls: String,
      typeName:String
    },
    computed: {
      objData () {
        // debugger
        return this.$parent.objData;
      }
    },
    methods: {
      rowClasses (_index) {
        let _isChecked,_isHighlight,_isHover;
        _isChecked = this.objData[_index] && this.objData[_index]._isChecked;
        _isHighlight =this.objData[_index] && this.objData[_index]._isHighlight;
        _isHover = this.objData[_index] && this.objData[_index]._isHover;
        return [
          `${this.prefixCls}-row`,
          this.rowClsName(_index),
          {
            [`${this.prefixCls}-row-checked`]: _isChecked,
            [`${this.prefixCls}-row-highlight`]:_isHighlight,
            [`${this.prefixCls}-row-hover`]:_isHover
          }
        ];
      },
      rowClsName (_index) {
        return this.$parent.$parent.rowClassName(this.objData[_index], _index);
      },
    },
    created() {
      // debugger
    }
  };
</script>