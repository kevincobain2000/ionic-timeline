### DEMO (codepen)

![alt tag](animate.gif)

http://codepen.io/kevincobain2000/pen/ZQWwOW

## How TO

### Copy Style.css


```
<link href="https://github.com/kevincobain2000/ionic-parallax-profile/master/www/css/style.css" rel="stylesheet">
```

Stylesheet is here = https://github.com/kevincobain2000/ionic-parallax-profile/tree/master/www/css


### Using it


#### HTML

See index.html

#### In your directives

```
.directive('headerShrink', function($document) {
  return {
    restrict: 'A',
    link: function($scope, $element, $attr) {
      var resizeFactor, scrollFactor, blurFactor;
      var header = $document[0].body.querySelector('.about-header');
      $scope.$on('userDetailContent.scroll', function(event,scrollView) {
        if (scrollView.__scrollTop >= 0) {
          scrollFactor = scrollView.__scrollTop/3.5;
          header.style[ionic.CSS.TRANSFORM] = 'translate3d(0, +' + scrollFactor + 'px, 0)';
        } else if (scrollView.__scrollTop > -70) {
          resizeFactor = -scrollView.__scrollTop/100 + 0.99;
          // blurFactor = -scrollView.__scrollTop/50;
          header.style[ionic.CSS.TRANSFORM] = 'scale('+resizeFactor+','+resizeFactor+')';
          // header.style.webkitFilter = 'blur('+blurFactor+'px)';
        }
      });
    }
  }
})
```