[![Build Status](https://travis-ci.org/devw/angular_test.svg)](https://travis-ci.org/devw/angular_test)

## Angualar Karma showcase

### Create the following directory structure

    > mkdir -p angular-karma-showcase/{app,test}
    > cd angular-karma-showcase
    
### Install third-party dependencies

    > bower init
    > bower install angular --save-dev
    > bower install angular-mocks --save-dev
    > bower install angular-resource --save-dev
    > bower install jasmine --save-dev
    > touche .gitignore # Git should ignore bower_components/*
    
### Run Jasmine on the browser

1. Create your test html file to see the results

        <-- spec-runner.html -->
        <link rel="stylesheet" href="./bower_components/jasmine/lib/jasmine-core/jasmine.css">
        <script src="./bower_components/jasmine/lib/jasmine-core/jasmine.js"></script>
        <script src="./bower_components/jasmine/lib/jasmine-core/jasmine-html.js"></script>
        <script src="./bower_components/jasmine/lib/jasmine-core/boot.js"></script>
    
2. Create your first html file to see the results

        /*test/simple.spec.js*/
        /*global describe, beforeEach, it*/
        describe('Simple test', function() {
            it('should be true...', function() {
                expect(true).toBeTruthy();
            });
        });
        

### Example code of an angular controller 
    
    // app/controllers/password.controller.js 
    // Inline Array Annotation
    app.controller('passwordController', ['$scope', function PasswordController($scope) {
        'use strict';
    
        $scope.password = '';
        $scope.strength = 'weak';
    
        $scope.grade = function() {
    
            var size = $scope.password.length;
    
            if (size > 8) {
                $scope.strength = 'strong';
            } else if (size > 3) {
                $scope.strength = 'medium';
            } else {
                $scope.strength = 'weak';
            }
        };
    
    }]);

### Testing angular controller

    /*global describe, beforeEach, it*/
    describe('MyControllerToTest', function () {
        var myController;
        var $scope;
    
        beforeEach(function () {
            angular.mock.module('myApp');
    
            angular.mock.inject(function($controller, $rootScope){
                $scope = $rootScope.$new();
                myController = $controller('myController', { 
                    $scope: $scope 
                });;
            });
        });
    
        describe('$scope.myMethod', function () {
            it('Describe what your method should do', function() {
                // test code
            });
        });
    });
    
### Create the package.json file

    > npm init
    
### Suggestions 
  
  1. To install tree command

        # OSx Users
        > brew install tree
        > sudo port install tree
        > fink install tree
        
        # Windows OS
        > export PATH=/c/Windows/System32/:$PATH
