```
defaults write com.apple.screencapture name "SS"

killall SystemUIServer

defaults write com.apple.screencapture "include-date" 0

killall SystemUIServer

defaults write com.apple.screencapture include-date -bool false

killall SystemUIServer

defaults write com.apple.screencapture "include-date" 1

killall SystemUIServer

```