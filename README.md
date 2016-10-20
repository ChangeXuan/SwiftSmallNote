# SwiftSmallNote
- UILabelView的自动获取高度(label.sizeThatFits()),这个函数虽然会自动获取label上文本的高度，但是英文和中文的字体高度是不同的，所以需注意
- UIImageView加载图片时，如果是用(named:"xxx")加载，那加载的图片会被放在缓存里，并且这块缓存区的数据，并不会遵循ARC内存管理方式，也就是说即使目前应用没有任何拥有该内存区域的对象了，这块内存区域也不会被释放，只有当应用周期结束（应用退出），该内存区域才会被释放。所以当加载不必要的图片时，建议使用(contentsOfFile:)
- 在tableView内容比较少时，可以不用重用机制http://www.faceye.net/search/82604.html#bottom-ad
- 图标问题，使用图标的时候，所选取的图标最好于app里的图标大小接近，否则可能会存在锯齿
- 虽然我比较喜欢使用tableView来做长内容的显示，但真相是，使用scrollerView可能会更优。
- storybord肯定是一个好工具，只是我还没会充分的使用
