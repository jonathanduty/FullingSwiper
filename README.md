![Png](https://github.com/ikemai/FullingSwiper/blob/master/assets/logo.png?raw=true)

[![CI Status](http://img.shields.io/travis/ikemai/FullingSwiper.svg?style=flat)](https://travis-ci.org/ikemai/FullingSwiper)
[![Version](https://img.shields.io/cocoapods/v/FullingSwiper.svg?style=flat)](http://cocoapods.org/pods/FullingSwiper)
[![License](https://img.shields.io/cocoapods/l/FullingSwiper.svg?style=flat)](http://cocoapods.org/pods/FullingSwiper)
[![Platform](https://img.shields.io/cocoapods/p/FullingSwiper.svg?style=flat)](http://cocoapods.org/pods/FullingSwiper)

![Gif](https://github.com/ikemai/FullingSwiper/blob/master/assets/fullingSwiper.gif?raw=true)

## Usage

To run the example project, clone the repo, and run `pod install` from the Example directory first.

## Requirements

* swift 2.0, iOS8.0 ~

## Installation

FullingSwiper is available through [CocoaPods](http://cocoapods.org). To install it, simply add the following line to your Podfile:

```ruby
pod "FullingSwiper"
```

# Example

It is the library which becomes able to return in `Stack View` in entire surface wipe.

## Default Set

```swift
if let pushView = pushViewController, navigationController = navigationController {
    pushView.fullingSwiper
        .set(navigationController: navigationController)
    navigationController.pushViewController(pushView, animated: true)
}
```

## Set Handlers

Set 'popViewController' handler
Set 'shouldBeginGesture' handler
Set 'completed' handler

```swift
fullingSwiper
    .set(navigationController: navigationController)
    .poping() { _ in
        print("Poping!")
    }
    .shouldBeginGesture() { _ in
        print("shouldBeginGesture!")
    }
    .completed() { _ in
        print("completed!")
    }
```

## Set Paramators

Param hideRatio is the value that less than hideRatio cancel pop. Default is 0.2.
Param duration is the time when (pop or push) animation. Default is 0.3.
Param scale is under view scale when (pop or push) animation. Default is 1.

```swift
pushView.fullingSwiper
    .set(navigationController: navigationController)
    .hideRatio(0.3)
    .animateDuration(0.1)
    .animateScale(0.95)
```

# Point to be noted
## When You set `stack view` more than two
Please set `fullingSwiper.reset()` by all means in `viewDidAppear`

```
override func viewDidAppear(animated: Bool) {
    super.viewDidAppear(animated)

    // ☆ Set
    fullingSwiper.reset()
}
```

## When you support iOS8
Please do not set fullingSwiper in viewWillAppear

```
override func viewWillAppear(animated: Bool) {
    super.viewWillAppear(animated)

    // ☆ Do not set
    if let navigationController = navigationController {
        fullingSwiper.set(navigationController: navigationController)
    }
}
```

# Author

ikemai

# License

FullingSwiper is available under the MIT license. See the LICENSE file for more info.
