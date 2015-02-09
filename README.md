# Cascading-Selected-Box-in-AngularJS
Creating Dependable Select Boxex using AngularJS , PHP with MySQL

Creating a Select Box in AngularJS is 


<div>
           <b>Choose Your Medical System :</b> <select name="selMedsys"  ng-change="cleargetDisease(); getDisease(Medsys);" ng-model="Medsys" ng-options="Medsys as Medsys.name for Medsys in Medsyss" ></select>
          </div>
            
            here in above select box, the options are loading from the database using PHP with MySQL... For this task we need to write one javascript file to load from the database... 
            
            $scope.getMedsysName = function () {
        $scope.status = 'Loading Medical System Categories...';
        $http.get('server/getData.php?r=Medsyss')
        .success (function(data, status, header, config) {
						   //alert(data);
            //console.log('Data Length: ' + data);
            $scope.status = 'Medsys Categories are loaded';
            $scope.Medsyss = data;
		
            })
        .error (function(data, status, header, config) {
            $scope.status = 'Something went wrong while loading Medical System Categories...';
            console.log('Error: ' + data);
            }) ;
    };
          
          By using JavaScript File the data will be loaded into select box and next I am proceeding with creation of another select box, But the second select box has to populated with the option selected in the first select box, For this task I am writing ng-hide in the second select box. The code as follows...
          
          <select name="selDisease" ng-hide="!Medsys || Medsys.id <= 0" ng-model="Disease"  ng-change="cleargetxyz(); getxyz(Medsys);">
                <option ng-repeat="Disease in Diseases" value=" {{ Disease.name }} "> {{ Disease.name }}</option>
            </select>
            
            
