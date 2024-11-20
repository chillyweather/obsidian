# Tables

#html #table 

The `<table>` element contains a number of nested elements to denote all the rows and cells in the table. Each row is marked with a set of `<tr></tr>` (table row) tags. Each cell in the row is marked with a set of `<td></td>` (table data) tags. In the top row of the table, the cells are marked with `<th></th>` (table header) tags.

```html
<table>
        <tr> <!-- first row with headers - break into cells with th tags -->
            <th>row 1 cell 1 - header of the first column</th> 
            <th>row 1 cell 2 - header of the second column</th>
            <th>row 1 cell 3 - header of the third column</th>
        </tr>
        <tr> <!-- the second and subsequent lines are for content - break them with td tags -->
            <td>row 2 cell 1</td>
            <td>row 2 cell 2</td>
            <td>row 2 cell 3</td>
        </tr>
        <tr>
            <td>row 3 cell 1</td>
            <td>row 3 cell 2</td>
            <td>row 3 cell 3</td>
        </tr>    
        <tr>
            <td>row 4 cell 1</td>
            <td>row 4 cell 2</td>
            <td>row 4 cell 3</td>
        </tr>    
</table>
```

We can merge cells using the `rowspan` and `colspan` attributes. Adding `colspan="3"` to the opening `<td>` tag means that the cell will run across three columns. As a result, this row will contain two fewer cells than the others.

```html
<table>
  <tr>
    <th></th>
    <th></th>
    <th></th>
    </tr>
  <tr>
    <td colspan="3">Table cell</td> <!-- there is only 1 cell in this row -->
    </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>
```