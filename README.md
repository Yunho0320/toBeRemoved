columnDefs: [
  {
    field: 'name',
    rowSpan: function(params) {
      const data = params.data;
      const rowIndex = params.node.rowIndex;
      const value = data.name;

      // Don't span if value is empty
      if (!value) return 1;

      // Check if previous row had same value
      if (
        rowIndex > 0 &&
        params.api.getDisplayedRowAtIndex(rowIndex - 1)?.data.name === value
      ) {
        return 0; // skip rendering — it was merged above
      }

      // Count how many rows should be merged
      let span = 1;
      for (let i = rowIndex + 1; i < params.api.getDisplayedRowCount(); i++) {
        const nextRow = params.api.getDisplayedRowAtIndex(i);
        if (nextRow?.data.name === value) {
          span++;
        } else {
          break;
        }
      }
      return span;
    },
    cellClass: 'merge-cell'
  },
  { field: 'model' },
  { field: 'price' }
]
