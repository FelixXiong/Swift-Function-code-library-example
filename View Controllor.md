### View Controllor

###### 设置视图控制器的背景色

```swift
self.view.backgroundColor = UIColor(red:255/255,green:255/255,blue:255/255,alpha:1) 
```

#### Navigition Bar

###### 设置Navigition Bar图片

```swift
self.navigationController?.navigationBar.setBackgroundImage(UIImage(named: "Background"), for: UIBarMetrics.default)
```

###### 隐藏状态栏

```swift
override var prefersStatusBarHidden: Bool {
    return true
}
```

##### Large Titles

为普通的Navigition Bar Title设置为大标题，在首View Contrllor.swift文件中编写下列代码：

```swift
     /*可选
     setupNavBar()
}
func setupNavBar(){
     */
            navigationController?.navigationBar.prefersLargeTitles = true
        }
```

如果不想持续每个视图大标题，则在其他View Contrllor.swift文件中编写下列代码：

```swift
navigationItem.largeTitleDisplayMode = .always
                                       .automatic
                                       .never
```

- .always ：总是大标题
- .automatic：如果前一个是大标题，将会保持；若前面不是大标题，将会变小
- .never：总不变大

#### Text

###### 设置字体颜色

```swift
label.textColor = UIColour.blackColour()
```

### 
