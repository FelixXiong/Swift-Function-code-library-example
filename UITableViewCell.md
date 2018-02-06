# UITableViewCell

### 属性：高度等

##### 设定行高度

```swift
    func tableView(_ tableView: UITableView, heightForRowAt indexPath: IndexPath) -> CGFloat {
        return 100
    }
```
### 选中行的操作

###### 为行打checkmark

```swift
if tableView.cellForRow(at: indexPath)?.accessoryType == UITableViewCellAccessoryType.checkmark//（没有if）仅有这行再次点击不消失
    {
        tableView.cellForRow(at: indexPath)?.accessoryType = UITableViewCellAccessoryType.none//如果是之前为checkmark，则设置none取消
    }
    else
    {
        tableView.cellForRow(at: indexPath)?.accessoryType = UITableViewCellAccessoryType.checkmark//如果之前没有勾，需要打一个
    }
```

### 行编辑与移动

##### 编辑和删除行

```swift
 override func tableView(_ tableView: UITableView, commit editingStyle: UITableViewCellEditingStyle, forRowAt indexPath: IndexPath) {
        if editingStyle == .delete {
            //从数据源中删除行
            tableView.deleteRows(at: [indexPath], with: .fade)
        } else if editingStyle == .insert {
            //创建适当类的新实例，将其插入到数组中，然后向表视图添加新行
```

##### 移动行、重新排序

允许重新排序单元格，如果返回否则无法重新排序

```swift
func tableView(_ tableView: UITableView, canMoveRowAt indexPath: IndexPath) -> Bool {
        return true
    }
```

执行行重排的操作

```swift
func tableView(_ tableView: UITableView, moveRowAt sourceIndexPath: IndexPath, to destinationIndexPath: IndexPath) {
   }
```
