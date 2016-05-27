# angular dayparts

Angular directive for select hours in a week

Code based on [this StackOverflow answer](http://stackoverflow.com/questions/23163952/how-do-i-capture-table-td-elements-using-mousedown-dragselect-event)


![Sample](sample.jpg)


Install it with Bower or npm

```bash
bower install angular-dayparts
```
```bash
npm install angular-dayparts
```


Include the module in your app

```javascript
angular.module('myapp', ['angular-dayparts'])
```


Configure the directive inside the controller

```javascript
$scope.options = {
    // Reset button
    reset: true, // default false
    
    // Event triggered when selecting a cell
    onChange: function(selected) {
        console.log('selected: ', selected)
    },
    
    // Prepopulated cells
    selected: ['monday-14', 'monday-15'],
    
    // When true clicking on the day name it will select the entire row
    disableRowSelection: true, // default false
    
    // When true clicking on the hour it will select the entire columns
    disableColumnSelection: true // default false
};
```
Declare a manual reload function in your controller and assign it to reload attribute on the directive. Optional.
```
<!-- in html -->
<angular-dayparts options="options" reload="reload"></angular-dayparts>
```

```
/*in controller*/
$scope.reload;
$scope.options.selected = ['monday-14', 'monday-15'];

function changeSelected() {
    //update selected
    $scope.options.selected = ['monday-14', 'monday-16']
    //reload
    if ($scope.reload) {
        $scope.reload();
    }
}

```


Call the directive from your page

```html
<angular-dayparts options="options" reload="reload"></angular-dayparts>
```


## License

Released under the terms of MIT License.