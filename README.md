# TaskMoveOnMulti-Screen
车载多屏画面拖动到另一屏幕实现<br>
环境：aosp 13<br>
1 move-to-other.patch ---这个实现的是多屏互动没有动画的版本<br>
2 move-to-other-display-animation.patch ---多屏互动有动画完美支持屏幕大小一样多屏情况，屏幕大小不一样也支持<br>
3 get_active_buffer_width.patch  ---获取surfaceflinger层面layer的实际buffer大小<br>

核心点<br>
1、屏幕1的镜像Task创建<br>
 copyTaskBuffer = SurfaceControl.mirrorSurface(rootTask.getSurfaceControl());<br>
2、画面移动过程，两边背景是黑的，解决方法让Activity下面的task显示<br>
otherTopActivity.mLaunchTaskBehind = true；<br>
