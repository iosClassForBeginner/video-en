# Code Together: Let's make iPhone app in an hour

  <div style="text-align:center"><img src ="https://github.com/iosClassForBeginner/video-en/blob/master/gifs%2Bimgs/demo.gif" width="50%" height="50%"/></div>  

  Thank you for visiting our account. We are going to make a simple video player app in an hour. If would you like to study yourself before hands-on, or review what you have learned in the session, please use the following material.

## Meetup
We are providing free hands-on on a monthly basis

https://www.meetup.com/iOS-Development-Meetup-for-Beginner/

## Development Environment
  Xcode 9 / Swift 4
  
  ・<a href="https://github.com/learn-co-students/reading-ios-intro-to-xcode-qa-public-001">What is Xcode?</a>

# Full procedure

## 0, Create your project

> Open Xcode  
> Select "Create a new Xcode project"  
> Select "Single View Application" and then tap "Next"  
> Fill "Product name" and then tap "Next"  
> Select the place for saving your project and then tap "Create"  

## 1, Collect Resources

1-1. Drop your icons into your "Assets.xcassets"

Get icons from [here](https://github.com/iosClassForBeginner/video-en/tree/master/icons) or you can get your favoirte icons from [here](https://www.flaticon.com/)

> <details><summary>How to add icons to the Assets folder</summary><div style="text-align:center"><img src ="https://github.com/iosClassForBeginner/video-en/blob/master/gifs%2Bimgs/0.gif" /></div></details>

## 2, Design your app

#### 🗂 Main.storyboard

2-1. Add video player based view to the storyboad
> <details><summary>How to add UIView to the storyboard</summary><div style="text-align:center"><img src ="https://github.com/iosClassForBeginner/video-en/blob/master/gifs%2Bimgs/1.gif" /></div></details>

2-2. Add play, stop and retry button, content mode and Autosizing
> <details><summary>How to add button to the storyboad</summary><div style="text-align:center"><img src ="https://github.com/iosClassForBeginner/video-en/blob/master/gifs%2Bimgs/2.gif" /></div></details>
> <details><summary>How to set image to the button</summary><div style="text-align:center"><img src ="https://github.com/iosClassForBeginner/video-en/blob/master/gifs%2Bimgs/3.gif" /></div></details>

Your storyboard may looks like this
<div style="text-align:center"><img src ="https://github.com/iosClassForBeginner/video-en/blob/master/gifs%2Bimgs/4.png" width="30%" height="30%"/></div>  

## 3, Connect to the ViewController

#### 🗂 Main.storyboard -> ViewController.swift

3-1. Connect outlets

★ control + drag in storyboard to create a control segue

> <details><summary>How to connect outlet</summary><div style="text-align:center"><img src ="https://github.com/iosClassForBeginner/video-en/blob/master/gifs%2Bimgs/5.gif" /></div></details>

3-2. Connect Actions

> <details><summary>How to connect actions</summary><div style="text-align:center"><img src ="https://github.com/iosClassForBeginner/video-en/blob/master/gifs%2Bimgs/7.gif" /></div></details>

## 4, Add code blocks in ViewController.swift

★ It's preferable to write following code yourself. It will help you to understand code more.

```Swift
import UIKit
import AVKit
import AVFoundation

class ViewController: UIViewController {
  
  @IBOutlet var playerView: UIView!
  var player: AVPlayer!
  var playerLayer: AVPlayerLayer!
  
  override func viewDidLoad() {
    super.viewDidLoad()
    initPlayer()
  }
  
  func initPlayer() {
    let videoUrl = URL(string: "https://clips.vorwaerts-gmbh.de/big_buck_bunny.mp4")
    player = AVPlayer(url: videoUrl!)
    playerLayer = AVPlayerLayer(player: player)
    playerView.layer.addSublayer(playerLayer)
  }
  
  override func viewDidLayoutSubviews() {
    playerLayer.frame = playerView.bounds
  }
  
  @IBAction func play(_ sender: Any) {
    player.play()
  }
  
  @IBAction func stop(_ sender: Any) {
    player.pause()
  }
  
  @IBAction func retry(_ sender: Any) {
    player.seek(to: kCMTimeZero)
  }
}
```
