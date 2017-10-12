MPAndroidChart
#### 介绍
开源，是Android的强大且易于使用的图表库

项目地址：https://github.com/PhilJay/MPAndroidChart

#### 导入
1. Gradle dependency (recommended)

Add the following to your project level build.gradle:
allprojects {
    repositories {
        maven { url "https://jitpack.io" }
    }
}
Add this to your app build.gradle:
dependencies {
    compile 'com.github.PhilJay:MPAndroidChart:v3.0.2'
}

其它

#### 文档
https://github.com/PhilJay/MPAndroidChart/wiki

#### 需求
* 一周内任务类别数量（已完成，未完成，待完成）——饼图PieChart
* 每日任务完成率
    因为是近期任务完成率，显示7天，原定平滑LineChart显示效果并不好，还是BarChart。
* 近6个月任务完成率——条形图
    数据量大，平滑LineChart。
* 每日添加任务数量——条形图 BarChart2D

#### 实例1：SemiAnnualChart


