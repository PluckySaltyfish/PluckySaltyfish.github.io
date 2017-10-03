UUID表示一个不变通用唯一标识符,代表一个128位的值
fragement UI
在activity代码中添加fragment。
###布局
* style
样式文件。规定固定样式，放在valuse/styles下，由`style`属性添加。
* margin
边距：组件与父容器的距离
内边距（padding）：组件与包含内容的距离

### xml
* activity_fragment.xml——统一的托管fragment，具有FrameLayout的布局
* fragment_crime.xml——布局文件
* fragment_crime_list.xml——(RecyclerView)
* 


### java
* Crime.java——模型层，定义crime的ID和title
* CrimeActivity.java——继承FragmentActivity
* CrimeFragment.java——控制模型与视图层的交互
* CrimeListActivity.java——继承FragmentActivity
* CrimeListFragment.java
* SimpleFragmentActivity.java


### RecycleList
RecyclerView的回收和定位屏幕上的组件
### ViewHolder和Adaptor
ViewHolder容纳View视图
adapter   
* 创建必要的ViewHolder 
* 绑定ViewHolder至模型数据层
### FragmentManager
负责管理fragment，将它们的视图添加到activity中，在activity中
声明。

* 管理fragment队列
* 管理fragment回退栈

```java
    Fragment fragment = fm.findFragmentById(R.id.fragment_container);
    if (fragment == null) {
        fragment = new CrimeFragment();
        fm.beginTransaction()
            .add(R.id.fragment_container, fragment)
            .commit();
```



