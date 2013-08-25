cb-ko-chosen
============

binding format

data-bind = "table: {

    chosenOption: *** or {***} //the option passed to chosen function when create the chosen

    source: ***, //source items

    valueProp: *** //the property of the items in source that will be used as the value of the option

    selectedValue: *** //the value that user is selected, it can be array

    selectedValueItemProp: the prop of the items in selectedValue array, that will be used to match the value in source

    displayProp: the property of the items in source that will be used as the text of the option

}"

Demo Html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
    <title></title>
    <link href="Content/chosen.css" rel="stylesheet">
    <script type="text/javascript" src="Scripts/jquery-1.8.3.js"></script>
    <script type="text/javascript" src="Scripts/knockout-2.3.0.debug.js"></script>
    <script type="text/javascript" src="Scripts/chosen.jquery.js"></script>
    <script type="text/javascript" src="Scripts/cb-ko-binding-chosen.js"></script>
</head>
<body>
    <div>
        <label>This is a demo select</label>
        <select style="width: 300px;" data-bind="chosen: { source: allCities, selectedValue: selectedCity, displayProp: 'name' }" ></select>
    </div>
    <div>
       You select City&nbsp;<span data-bind="text: selectedCity().name"></span>, It's temperature is&nbsp;<span data-bind="    text: selectedCity().temperature" />
    </div>
    <script type="text/javascript">
        var ViewModel = function () {
            this.allCities = ko.observableArray([
                { name: 'Wellington', temperature: '22' },
                { name: 'Sydeny', temperature: '25' },
                { name: 'Melbourne', temperature: '20' },
                { name: 'Beijing', temperature: '35' }]);
            this.selectedCity = ko.observable();
        };
        $("body").ready(function () {
            ko.applyBindings(new ViewModel());
        });
    </script>
</body>
</html>
