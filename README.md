# ImagePickerSheetController.

## About
ImagePickerSheetController is a component that replicates the custom photo action sheet in iMessage. It's very similar to UIActionController which makes its usage simple and concise.

![Screenshot](https://raw.githubusercontent.com/larcus94/ImagePickerSheetController/master/Screenshots/GoT.gif)

[![Twitter: @larcus94](https://img.shields.io/badge/contact-@larcus94-blue.svg?style=flat)](https://twitter.com/larcus94)
[![License](http://img.shields.io/badge/license-MIT-green.svg?style=flat)](https://github.com/larcus94/ImagePickerSheetController/blob/master/LICENSE)
[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)

## Author
I'm Laurin Brandner, I'm on [Twitter](https://twitter.com/larcus94).

## Usage
`ImagePickerSheetController` is similar to `UIActionController` in its usage.

### Example

```swift
let controller = ImagePickerSheetController()
controller.addAction(ImageAction(title: NSLocalizedString("Take Photo Or Video", comment: "Action Title"), secondaryTitle: NSLocalizedString("Add comment", comment: "Action Title"), handler: { _ in
	presentImagePickerController(.Camera)
}, secondaryHandler: { _, numberOfPhotos in
	println("Comment \(numberOfPhotos) photos")
}))
controller.addAction(ImageAction(title: NSLocalizedString("Photo Library", comment: "Action Title"), secondaryTitle: { NSString.localizedStringWithFormat(NSLocalizedString("ImagePickerSheet.button1.Send %lu Photo", comment: "Action Title"), $0) as String}, handler: { _ in
	presentImagePickerController(.PhotoLibrary)
}, secondaryHandler: { _, numberOfPhotos in
	controller.getSelectedImagesWithCompletion() { images in
		println("Send \(images) photos")
	}
}))
controller.addAction(ImageAction(title: NSLocalizedString("Cancel", comment: "Action Title"), style: .Cancel, handler: { _ in
	println("Cancelled")
}))
            
presentViewController(controller, animated: true, completion: nil)
```
It's recommended to use [stringsdict](https://developer.apple.com/library/ios/documentation/MacOSX/Conceptual/BPInternational/StringsdictFileFormat/StringsdictFileFormat.html) to easily translate plural forms in any language.

## Installation

### CocoaPods
```ruby
pod "ImagePickerSheetController", "~> 0.1.2"
```

###Carthage
```objc
github "larcus94/ImagePickerSheetController" ~> 0.1.2
```


## Requirements
ImagePickerSheetController is written in Swift and links against `Photos.framework`. It therefore requires iOS 8 or later.

## License
ImagePickerSheetController is licensed under the [MIT License](http://opensource.org/licenses/mit-license.php).
