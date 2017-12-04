##Activity跳转动画实现方式
1. overridePendingTransition(R.anim.slide_in_lef,R.anim.slide_out_right);

		<?xml version="1.0" encoding="utf-8"?>
		<set xmlns:Android="http://schemas.Android.com/apk/res/Android"
		    Android:shareInterpolator="false"
		    Android:zAdjustment="top">
		    <translate
		        Android:duration="200"
		        Android:fromXDelta="-100.0%p"
		        Android:toXDelta="0.0" />
		</set>

2.使用style的方式定义Activity的切换动画

	windowAnimationStyle	

	<style name="AppTheme" 	parent="Theme.AppCompat.Light.DarkActionBar">
        <!-- Customize your theme here. -->
        <item name="colorPrimary">@color/colorPrimary</item>
        <item name="colorPrimaryDark">@color/colorPrimaryDark</item>
        <item name="colorAccent">@color/colorAccent</item>
        <item name="Android:windowAnimationStyle">@style/activityAnim</item>
    </style>

	<!-- 使用style方式定义activity切换动画 -->
    <style name="activityAnim">
        <item name="Android:activityOpenEnterAnimation">@anim/slide_in_top</item>
        <item name="Android:activityOpenExitAnimation">@anim/slide_in_top</item>
    </style>

	windowAnimationStyle中存在四种动画：

	activityOpenEnterAnimation // 用于设置打开新的Activity并进入新的Activity展示的动画
	activityOpenExitAnimation  // 用于设置打开新的Activity并销毁之前的Activity展示的动画
	activityCloseEnterAnimation  // 用于设置关闭当前Activity进入上一个Activity展示的动画
	activityCloseExitAnimation  // 用于设置关闭当前Activity时展示的动画

3 使用ActivityOptions切换动画实现Activity跳转动画
