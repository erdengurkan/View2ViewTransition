# View2ViewTransition

[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-brightgreen.svg)](https://github.com/Carthage/Carthage) ![Pod Version](https://img.shields.io/badge/Pod-0.0.4-blue.svg) ![Swift Version](https://img.shields.io/badge/Swift-2.2-orange.svg) ![License MIT](https://img.shields.io/badge/License-MIT-lightgrey.svg) ![Plaforms](https://img.shields.io/badge/Platform-iOS-lightgrey.svg)

Simple framework for custom interactive viewController transition from one view to another view.

<img src="https://github.com/naru-jpn/View2ViewTransition/blob/master/preview.gif?raw=true" width="300">

## installation

__Carthage__

```
github "naru-jpn/View2ViewTransition"
```

__CocoaPods__

```
pod 'View2ViewTransition'
```

## Usage

__Create TransitionController and implement presentation__

```swift
// Create TransitionController
var transitionController: TransitionController = TransitionController()

// ...

// Present view controller with transition delegate
let presentedViewController: PresentedViewController = PresentedViewController()
presentedViewController.transitioningDelegate = transitionController

transitionController.present(viewController: presentedViewController, on: self, attached: presentedViewController, completion: nil)
```

__Presenting viewController conforms View2ViewTransitionPresenting__

```swift
func initialFrame(userInfo: [String: AnyObject]?, isPresenting: Bool) -> CGRect
func initialView(userInfo: [String: AnyObject]?, isPresenting: Bool) -> UIView
func prepereInitialView(userInfo: [String: AnyObject]?, isPresenting: Bool) -> Void // (optional)
```

__Presented viewController conforms View2ViewTransitionPresented__

```swift
func destinationFrame(userInfo: [String: AnyObject]?, isPresenting: Bool) -> CGRect
func destinationView(userInfo: [String: AnyObject]?, isPresenting: Bool) -> UIView
func prepareDestinationView(userInfo: [String: AnyObject]?, isPresenting: Bool) -> Void // (optional)
```

### Use UserInfo

You can set userInfo to notify indexPath or share resource etc.

```swift
transitionController.userInfo = ["key": "value", ...]
```

### Debug Mode

If you have hierarchical view controllers (navigation controllers) in app, viewController to conform protocol is not intuitive. View2ViewTransition prints some information in debug mode. 

```swift
let transitionController = TransitionController()
// ...
transitionController.debuging = true
```

## Example

[View2ViewTransitionExample](https://github.com/naru-jpn/View2ViewTransition/tree/master/Example/View2ViewTransitionExample)
