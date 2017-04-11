# WHC_AutoLayout
<div align=center><img src="https://github.com/netyouli/WHC_AutoLayoutKit/blob/master/Gif/WHC_AutoLayoutLogo.png"/></div></br>

![Build Status](https://api.travis-ci.org/netyouli/WHC_AutoLayoutKit.svg?branch=master)
[![Pod Version](http://img.shields.io/cocoapods/v/WHC_AutoLayoutKit.svg?style=flat)](http://cocoadocs.org/docsets/WHC_AutoLayoutKit/)
[![Pod Platform](http://img.shields.io/cocoapods/p/WHC_AutoLayoutKit.svg?style=flat)](http://cocoadocs.org/docsets/WHC_AutoLayoutKit/)
[![Pod License](http://img.shields.io/cocoapods/l/WHC_AutoLayoutKit.svg?style=flat)](https://opensource.org/licenses/MIT)

-  IOS platforms currently in use the fastest the simplest development to build the UI layout automatically open source library, strong dynamic layout constraint handling capacity
-  Service to update constraints, convenient and quick dynamic UI layout.


Introduce
==============
-  Adopt chain layout Api calls convenient
-  Include one line of code to calculate UITableViewCell highly module
-  Contains WHC_StackView module (UIStackView purpose alternative system)
-  Automatic identification of the same type conflict and update the new constraints
-  Support change constraints priority
-  Support delete constraints

Require
==============
* iOS 8.0 or later
* Xcode 8.0 or later

Install
==============
* CocoaPods: pod 'WHC_AutoLayoutKit'

Usage
==============

## Automatic height view
![](https://github.com/netyouli/WHC_AutoLayoutKit/blob/master/Gif/autoHeight.gif)

```objective-c
view.whc_LeftSpace(10)
    .whc_TopSpace(10)
    .whc_RightSpace(10)
    .whc_HeightAuto();
```

## Update the view constraints

Modify the view to the left from 20 other views
```objective-c
view.whc_LeftSpaceToView(20,otherView);
```

## Remove the constraint

Remove all constraints associated with view left
```objective-c
view.whc_RemoveLayoutAttrs(NSLayoutAttributeLeft);
```
To remove multiple constraints associated with view
```objective-c
view.whc_RemoveLayoutAttrs(NSLayoutAttributeLeft,NSLayoutAttributeLeading,NSLayoutAttributeTop);
```

## Modify the view constraint priority

Modify the view constraint for low priority right
```objective-c
view.whc_RightSpace(10)
    .whc_PriorityLow();
```

## One line of code calculation cell height

No reuse way calculated cell height
```objective-c
- (CGFloat)tableView:(UITableView *)tableView heightForRowAtIndexPath:(NSIndexPath *)indexPath {
    return [UITableViewCell whc_CellHeightForIndexPath:indexPath tableView:tableView];
}
```

Reuse way calculated cell height
```objective-c
- (CGFloat)tableView:(UITableView *)tableView heightForRowAtIndexPath:(NSIndexPath *)indexPath {
    return [UITableViewCell whc_CellHeightForIndexPath:indexPath 
                                             tableView:tableView 
                                            identifier:@"kFirendsCircleCellIdentifier" 
                                           layoutBlock:^(UITableViewCell *cell) {
         /// use model layout cell
         [(FriendsCircleCell *)cell setFriendModel:_friendModelArray[indexPath.row]];
    }];
}
```
## Use WHC_StackView

Create WHC_StackView
```objective-c
WHC_StackView * stackView = [WHC_StackView new];
[self.view addSubview: stackView];
```

Add constraint
```objective-c
stackView.whc_LeftSpace(10)
         .whc_TopSpace(10)
         .whc_RightSpace(10)
         .whc_HeightAuto();
```

Configuration stackView
#### 1. Set the padding
```objective-c
stackView.whc_Edge = UIEdgeInsetsMake(10, 10, 10, 10); // 内边距
```
#### 2. Set the layout direction
```objective-c
stackView.whc_Orientation = Vertical;                  // 自动垂直布局
```
#### 3. Set the child views lateral clearance
```objective-c
stackView.whc_HSpace = 10;                             // 子视图横向间隙
```
#### 4. Set the child views vertical clearance
```objective-c
stackView.whc_VSpace = 10;                             // 子视图垂直间隙
```
#### 5. Add subview and start the layout 
```objective-c
for (int i = 0; i < 4; i++) {
    UIView * view = [UIView new];
    [stackView addSubview:view];        
}
[stackView whc_StartLayout];
```
Prompt
==============

- For more UI layout automatically, WHC_StackView components, one line of code to calculate the cell height module, please download this demo to check the specific usage

Part of the WHC_AutoLayoutKit demo show
==============

<img src = "https://github.com/netyouli/WHC_AutoLayoutKit/blob/master/Gif/c.png" width = "375"><img src = "https://github.com/netyouli/WHC_AutoLayoutKit/blob/master/Gif/g.png" width = "375">
![](https://github.com/netyouli/WHC_AutoLayoutKit/blob/master/Gif/f.gif)![](https://github.com/netyouli/WHC_AutoLayoutKit/blob/master/Gif/a.gif)![](https://github.com/netyouli/WHC_AutoLayoutKit/blob/master/Gif/swiftb.gif)![image](https://github.com/netyouli/WHC_AutoLayoutKit/blob/master/Gif/d.png)

## Licenses
All source code is licensed under the MIT License.

