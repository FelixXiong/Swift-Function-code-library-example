# TableViewCell相关的实现功能的几个方式

## 实现编辑按钮进行开关提示词变化的几个方式

### 方式1

```Swift
@IBAction func EditButton(_ sender: Any) {
        
        ListTableView.isEditing = !ListTableView.isEditing
        switch WillLearnListTableView.isEditing{
        case true:
            EditButton.title = "done"
        case false:
            EditButton.title = "edit"
            
        }
```
参考链接：[How To Reorder/Rearrange Table View Cells In Xcode 8 (Swift 3)](https://www.youtube.com/watch?v=iym7P9jQmpU&t=604s)

### 方式2

```Swift
@IBAction func EditButton(_ sender: Any) {
        
        ListTableView.isEditing = !ListTableView.isEditing
        if ListTableView.isEditing{
            EditButton.title = "done"
            {
            else
            {
            EditButton.title = "edit"          
        }
```
参考链接：[Rearrange/Delete Table View (Swift4 + Xcode 9.0)](https://youtu.be/I9cJZiuYSO4)


## 实现移动行重排的几个方式

未确定以下方法的作用以及是否可替代

```Swift
 //移动行
    //是否可编辑
    func tableView(_ tableView: UITableView, canEditRowAt indexPath: IndexPath) -> Bool {
        return true
}
 // 编辑模式
    override func setEditing(_ editing: Bool, animated: Bool) {
        super.setEditing(editing, animated: animated)
        WillLearnListTableView.setEditing(editing, animated: true)
    }
```
### 方式1

```Swift
    //允许重新排序单元格，如果返回否则无法重新排序
    func tableView(_ tableView: UITableView, canMoveRowAt indexPath: IndexPath) -> Bool {
        return true
    }
    
    //执行行重排的操作
    func tableView(_ tableView: UITableView, moveRowAt sourceIndexPath: IndexPath, to destinationIndexPath: IndexPath){
        
        let item = Array[sourceIndexPath.row]
        
        Array.remove(at: sourceIndexPath.row)
        Array.insert(item, at: destinationIndexPath.row)
    }
```

参考链接：[How To Reorder/Rearrange Table View Cells In Xcode 8 (Swift 3)](https://www.youtube.com/watch?v=iym7P9jQmpU&t=604s)

### 方式2

```swift
 // Move the cell
  func tableView(_ tableView: UITableView, canMoveRowAt indexPath: IndexPath) -> Bool {
    return self.isEditing
  }
  
  func tableView(_ tableView: UITableView, moveRowAt sourceIndexPath: IndexPath, to destinationIndexPath: IndexPath) {
    let todo = todos.remove(at: (sourceIndexPath as NSIndexPath).row)
    todos.insert(todo, at: (destinationIndexPath as NSIndexPath).row)
  }
}
```

参考链接： [soapyigu/Swift-30-Projects/Project 04 - Todo/Todo.xcodeproj/](https://github.com/soapyigu/Swift-30-Projects/tree/master/Project%2004%20-%20Todo/Todo.xcodeproj)

