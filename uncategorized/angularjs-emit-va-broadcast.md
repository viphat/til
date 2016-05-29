---
layout: default
title: "AngularJS - $emit và $broadcast"
permalink: /:slug
tags: [angularjs, front-end]
---

Dạo này đang refactor lại toàn bộ Front-End của dự án đang làm. Thời gian trước code bừa bộn quá nên giờ là dịp để chỉnh đốn lại, nhằm giảm bớt được phần nào các Technical Debt đang mắc phải. Do vậy, lại có dịp học hỏi và rèn luyện thêm về AngularJS khi cố gắng tuân theo các Best Practice của nó (Trước đây cứ quăng dữ liệu vào $rootScope để mấy controller, directive, service "nói chuyện" với nhau >_<, giờ đỡ nhiều rồi.)

$rootScope.$emit only lets other $rootScope listeners catch it. This is good when you don't want every $scope to get it. Mostly a high level communication. Think of it as adults talking to each other in a room so the kids can't hear them.

$rootScope.$broadcast is a method that lets pretty much everything hear it. This would be the equivalent of parents yelling that dinner is ready so everyone in the house hears it.

$scope.$emit is when you want that $scope and all its parents and $rootScope to hear the event. This is a child whining to their parents at home (but not at a grocery store where other kids can hear).

$scope.$broadcast is for the $scope itself and its children. This is a child whispering to its stuffed animals so their parents can't hear.


AngularJS provides publish subscribe mechanism using using $emit and $broadcast mechanism.
A published message can be subscribed or listened using $on method.
In this demo, "We will learn the difference between Emit and broadcast pub-sub mechanism using a real simple example".
Difference between Emit and Broadcast is the way they propagate or traveled from the source.
A message publish via $emit propagates upward and travel up to $rootScope.scope.
A message published via $broadcast propagate downward towards the children scope.
Below code shows the demonstration of emit and broadcast.When you  press emit button the string typed in the input box published as a message and traveled upward and listened by the listener attached in GrandParentController. When you  press broad button the string typed in the input box published as a message and traveled downward and listened by the listener attached in ChildController.
http://www.tutorialsavvy.com/2014/09/angularjs-publish-subscribe-using-emit-and-broadcast.html/


https://www.quora.com/Is-it-a-bad-practice-to-always-use-broadcast-on-on-the-rootScope-in-AngularJS
