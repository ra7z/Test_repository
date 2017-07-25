#ng-app
#ng-model
#ng-bind
#controller declaration ng-controller

#controller definition in script
	<script>
  var app = angular.module('myApp', []);
  app.controller('myCtrl',function($scope){
    $scope.firstName = "John";
    $scope.lastName = "Wick";
  });
  
#scope 


#directive

	<!DOCTYPE html>
	<html>
	<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.4/angular.min.js"></script>
	<body>

	<p>Try to change the names.</p>

	<div ng-app="myApp" ng-controller="myCtrl" w3-Test-Directive>

	First Name: <input type="text" ng-model="firstName"><br>
	Last Name: <input type="text" ng-model="lastName"><br>
	<br>
	Address: <input type="text" ng-model="address"><br>


	<br>
	Full Name: {{firstName + " " + lastName}}
	<br>
	Address: {{address}}
	</div>

	<script>
	  var app = angular.module('myApp', []);
	  app.controller('myCtrl',function($scope){
		$scope.firstName = "John";
		$scope.lastName = "Wick";
	  });
	  app.directive("w3TestDirective", function() {
		return {
			template : "I was made in a directive constructor!"
			
		};
	});
	  
	</script>

	</body>
	</html>
	
	
#expressions

	<div ng-app="" ng-init="quantity=1;cost=5">

	<p>Total in dollar: {{ quantity * cost }}</p>

	</div>

	
#controllers and modules in files

	#_#index.html
			<!DOCTYPE html>
			<html>
			<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.4/angular.min.js"></script>
			<body>

			<div ng-app="myApp" ng-controller="myCtrl">
			{{ firstName + " " + lastName + " : " +address }}
			</div>

			<script src="myApp.js"></script>
			<script src="myCtrl.js"></script>

			</body>
			</html>
	#_#myApp.js
			var app = angular.module("myApp", []);
			
	#_#myCtrl.js
			app.controller("myCtrl", function($scope) {
			$scope.firstName = "John";
			$scope.lastName= "Doe";
			$scope.address= "22,Jump St.";
			});
			
	##_##Output: 
			John Doe : 22,Jump St.
			
			
#directive templates

		<!DOCTYPE html>
		<html>
		<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.4/angular.min.js"></script>
		<body ng-app="myApp">
		<input type="text" ng-model="texter"/>
		<w3-test-directive></w3-test-directive>
		<w2-tester-directive></w2-tester-directive>
		<script>
		var app = angular.module("myApp", []);
		app.directive("w3TestDirective", function() {
			return {
				template : "<h1>Made by a directive!</h1> {{texter}} <p>Woah</p>"
			};
		});
		app.directive("w2TesterDirective",function() {
			return {
				template : "this is a second template not generally {{texter}} used"	
			};
		});

		</script>

		</body>
		</html>
		
		
##directive invocations:
	###element name
	<w3-test-directive></w3-test-directive>
	
	###attribute
	<div w3-test-directive></div>
	
	###class
	<div class="w3-test-directive"></div>
	
		####Note:
			return {
				restrict : "C",
				template : "<h1>Made by a directive!</h1>"
			};
	
	###comment
	<!-- directive: w3-test-directive -->
		
		####Note:
			return {
				restrict : "M",
				replace : true,
				template : "<h1>Made by a directive!</h1>"
			};
##Directive restrictions:
		By adding a restrict property with the value "A", the directive can only be invoked by attributes.
		
		The legal restrict values are:

		E for Element name
		A for Attribute
		C for Class
		M for Comment
	By default the value is EA, meaning that both Element names and attribute names can invoke the directive.
	
## ng-model :: Validate User input 
		<!DOCTYPE html>
		<html>
		<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.4/angular.min.js"></script>

		<body>

		  <form ng-app="" name="myForm">
			Email:
			<input type="email" name="myAddress" ng-model="text">
			<span ng-show="myForm.myAddress.$error.email">Not a valid e-mail address</span>
		  </form>

		  <p>Enter your e-mail address in the input field. AngularJS will display an errormessage if the address is not an e-mail.</p>

		</body>

		</html>


	Angular also provides some help in this context. We can validate a form and see that the required validations work correctly. It provides different objects to the form. They are very helpful while validating forms:
	
	$pristine: It will be TRUE, if the user has not interacted with the form yet
	$dirty: It will be TRUE, if the user has already interacted with the form.
	$valid: It will be TRUE, if all containing form and controls are valid
	$invalid: It will be TRUE, if at least one containing form and control is invalid.
	$error: Is an object hash, containing references to all invalid controls or forms, where: 
	keys are validation tokens (error names)
	values are arrays of controls or forms that are invalid with given error.

	There are some built in validation tokens, that can help in validating form:

	email
	max
	maxlength
	min
	minlength
	number
	pattern
	required
	url

	In accordance with these AngularJS also provides corresponding CSS classes for them. We can use them for validation purpose.
	####@future uncovered checks::
		ng-pristine
		ng-dirty
		ng-valid
		ng-invalid

##Data Binding
##Controllers
